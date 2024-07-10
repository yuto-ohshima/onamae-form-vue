<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps<{
  firstName?: string
  lastName?: string
  onChangeFirstName?: (value: string) => void
  onChangeLastName?: (value: string) => void
}>()

const colObject = {
  display: 'grid',
  gap: '16px'
}

const firstNameInput = ref(props.firstName || '')
const changeFirstName = (event: Event) => {
  if (props.onChangeFirstName) {
    const value = (event.target as HTMLInputElement).value
    props.onChangeFirstName(value)
    firstNameInput.value = value
  }
}
const lastNameInput = ref(props.lastName || '')
const changeLastName = (event: Event) => {
  if (props.onChangeLastName) {
    const value = (event.target as HTMLInputElement).value
    props.onChangeLastName(value)
    lastNameInput.value = value
  }
}
</script>

<template>
  <div>
    <h1>お名前フォーム</h1>
    <div :style="colObject">
      <input v-model="firstNameInput" @input="changeFirstName" />
      <input v-model="lastNameInput" @input="changeLastName" />
    </div>
  </div>
</template>
