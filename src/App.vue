<template>
  <div>
      <input v-model='currentTodo' @keydown.enter='addTodo()' placeholder='Add a todo'>
      <ul class='todo'>
        <li v-for='todo in todos' :key='todo.id'>
          <input type='checkbox'>
            {{todo.label}}
            <button @click="removeTodo(todo)">Delete</button>
        </li>
      </ul>
  </div>
</template>

<script>


export default {
  data() {
    return {
      todos: [],
      currentTodo: ''
    }
  },
  methods: {
    addTodo() {
      this.todos.push({id:this.todos.length, label: this.currentTodo, completed: false});
      this.currentTodo = '';
    },
    removeTodo(todo) {
      var index = this.todos.indexOf(todo)
      this.todos.splice(index,1)
    },
    // completeTodo(todo) {
    //   this.todos
    // }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
