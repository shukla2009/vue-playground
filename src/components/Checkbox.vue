<template>
  <div>
    <div v-for='event in hooks.events' :key='event.id'>
      <input v-model='event.selected' type='checkbox' />
      <label>{{event.selected}}</label>
    </div>
    <button @click="save()">Save Me</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Checkbox",
  data() {
    return {
      hooks: null
    };
  },
  methods: {
    get: function() {
      axios
        .get("http://localhost:3000/hooks")
        .then(response => (this.hooks = response.data));
    },
    save: function() {
      axios
        .post("http://localhost:3000/hooks",this.hooks)
        .then(response => console.log(JSON.stringify(response)));
    }
  },
  mounted() {
    this.get();
  }
};
</script>

<style scoped>
</style>
