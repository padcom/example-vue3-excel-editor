<template>
  <VueExcelEditor v-model="users">
    <VueExcelColumn field="id" label="User ID" type="string" width="80px" />
    <VueExcelColumn field="lastName" label="Name" type="string" width="150px" />
    <VueExcelColumn field="phone" label="Contact" type="string" width="130px" />
    <VueExcelColumn field="gender" label="Gender" type="select" width="50px" :options="['F','M','U']" />
    <VueExcelColumn field="age" label="Age" type="number" width="70px" />
    <VueExcelColumn field="birthDate" label="Date Of Birth" type="date" width="130px" />
    <VueExcelColumn field="height" label="Height" type="number" width="80px" />
    <VueExcelColumn field="weight" label="Weight" type="number" width="80px" />
  </VueExcelEditor>
</template>

<script lang="ts" setup>
import { ref, onMounted } from 'vue'
import VueExcelEditor from './components/VueExcelEditor.vue'
import VueExcelColumn from './components/VueExcelColumn.vue'

const users = ref([])

onMounted(async () => {
  const response = await fetch('https://dummyjson.com/users')
  users.value = (await response.json()).users
})
</script>

<style lang="postcss" scoped>
.note {
  margin-top: 2.5rem;
}
</style>
