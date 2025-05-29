```
start_task(fun::Function)::Task
```

Create a new task from `fun` and schedule the task, similar to the `@task` macro. Also register a hook that shows exception and backtrace if the task fails.
