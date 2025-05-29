```
@wkspawn [:default|:interactive] expr
```

Create a `Task` and `schedule` it to run on any available thread in the specified threadpool (`:default` if unspecified). The task is allocated to a thread once one becomes available. To wait for the task to finish, call `wait` on the result of this macro, or call `fetch` to wait and then obtain its return value.

Values can be interpolated into `@wkspawn` via `$`, which copies the value directly into the constructed underlying closure. This allows you to insert the *value* of a variable, isolating the asynchronous code from changes to the variable's value in the current task.
