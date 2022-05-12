<template>
  <div>
    <h1>Test - environment</h1>
    <div v-for="item in items" :key="item.name">
      {{item.name}}
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import axios from 'axios'

export default Vue.extend({
  name: 'IndexPage',
  data() {
    return {
      items: [],
    }
  },
  created() {
    axios.get('http://localhost:3001/items')
      .then(response => {
        this.items = response.data
      })
      .catch(e => {
        console.log(e)
      })
  }
})
</script>
