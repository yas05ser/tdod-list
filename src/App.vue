<template>
  <div class="container">
    <form action="">
      <input type="text" placeholder="Type Your Task" v-model="taskText" />
      <button @click="addTask" :disabled="!taskText">Add Task</button>
      <button
        class="delete-all"
        v-if="tasks.length > 1"
        @click.prevent="deleteAll"
      >
        Delete All
      </button>
    </form>
    <div class="tasks-list" v-for="(task, index) in tasks" :key="index">
      <div class="task-box">{{ task.words }}</div>
      <span class="delete" @click="deleteTask(index)">Delete</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      tasks: [],
      taskText: "",
    };
  },
  methods: {
    addTask: function () {
      this.tasks.push({ words: this.taskText, done: false });
      this.taskText = "";
    },
    deleteTask: function (index) {
      this.tasks.splice(index, 1);
    },
    deleteAll: function () {
      this.tasks = [];
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
.container {
  margin-top: 150px;
  text-align: center;
}
form {
  margin: 20px auto 10px;
  width: 500px;
  overflow: hidden;
}

input {
  background-color: #f7f7f7;
  border: 1px solid #eee;
  margin-bottom: 15px;
  width: calc(100% - 210px);
  height: 46px;
  padding: 10px;
  float: left;
}
input:focus {
  outline: none;
}
button {
  width: 90px;
  height: 46px;
  padding: 10px;
  background-color: #2196f3;
  color: #fff;
  border-color: transparent;
  cursor: pointer;
  float: left;
  margin-left: 5px;
  button:disabled {
    opacity: 0.4;
    cursor: no-drop;
  }
  &:focus {
    outline: none;
  }
  &.delete-all {
    width: 110px;
    background-color: #f44336;
  }
}

.tasks-list {
  width: 500px;
  margin: 0 auto;
}
.task-box {
  background-color: rgba(139, 195, 74, 0.25);
  padding: 15px;
  text-align: left;
  margin-bottom: 15px;
  margin-right: 5px;
  width: calc(100% - 86px);
  cursor: pointer;
  float: left;
}
.delete {
  float: right;
  width: 80px;
  background-color: #f44336;
  color: #fff;
  border-color: transparent;
  padding: 1px 10px;
  cursor: pointer;
  height: 48px;
  line-height: 51px;
}
</style>
