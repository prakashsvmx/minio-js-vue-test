<template>
  <h2>List of Buckets</h2>
  <table border="1">
    <thead>
      <tr>
        <th>Name</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(product, index) in localProducts" :key="index">
        <td>{{ product.name }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import { defineComponent } from 'vue'
import { getBuckets } from '../utils/mc'


export default defineComponent({
  mounted() {
    setTimeout(async () => {

      const fewBuckets = await getBuckets();

      this.localProducts = fewBuckets.slice(1,10)
    }, 1000)
  },
  data() {
    return {
      localProducts: [],
    }
  }
})
</script>
