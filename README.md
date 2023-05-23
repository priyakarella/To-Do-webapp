# To-Do-webapp
<!DOCTYPE html>
<html>
<head>
  <title>Daily Tasks App</title>
  <link rel="stylesheet" type="text/css" href="todo.css">
</head>
<body "background-color:powderblue">
  <div class="container">
    <h1>Daily Tasks</h1>
    <form id="task-form">
      <input type="text" id="task-input" placeholder="Add a new task..." required>
      <button type="submit">Add Task</button>
    </form>
    <div id="task-list">
      <h2>Tasks</h2>
      <ul id="incomplete-tasks"></ul>
      <h2>Completed Tasks</h2>
      <ul id="completed-tasks"></ul>
    </div>
  </div>
  <script src="app.js"></script>
</body>
</html>
#CSS
.container {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
}

h1, h2 {
  text-align: center;
}

form {
  margin-bottom: 20px;
}

input[type="text"] {
  width: 70%;
  padding: 10px;
  font-size: 16px;
}

button {
  padding: 10px 20px;
  font-size: 16px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin-bottom: 10px;
}

.completed {
  text-decoration: line-through;
}
#JAVASCRIPT
document.getElementById('task-form').addEventListener('submit', function(event) {
  event.preventDefault();
  var taskInput = document.getElementById('task-input');
  var task = taskInput.value.trim();
  if (task !== '') {
    addTask(task);
    taskInput.value = '';
  }
});

function addTask(task) {
  var newTask = document.createElement('li');
  newTask.textContent = task;
  newTask.addEventListener('click', completeTask);
  document.getElementById('incomplete-tasks').appendChild(newTask);
}

function completeTask() {
  var task = this;
  task.removeEventListener('click', completeTask);
  task.classList.add('completed');
  document.getElementById('completed-tasks').appendChild(task);
}
