<script>
  // In composition API need to wrap everything in setup


  import {ref} from 'vue';

  export default {
   setup(){
    const name = ref("John Doe");
    const status = ref("active");
    const tasks = ref(['Task One', 'Task Two', 'Task Three']);

    const toggleStatus = () => {
      if(status.value === 'active') status.value = 'pending';
      else if(status.value === 'pending') status.value = 'inactive';
      else status.value = 'active';
    }

    return {
      name, status, tasks, toggleStatus
    }
   }
  }

</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is inactive</p>
  
  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks" :key="task">
      {{ task }}
    </li>
  </ul>

  <!-- <button v-on:click="toggleStatus">Change Status</button> -->
  <button @click="toggleStatus">Change Status</button>

</template>
