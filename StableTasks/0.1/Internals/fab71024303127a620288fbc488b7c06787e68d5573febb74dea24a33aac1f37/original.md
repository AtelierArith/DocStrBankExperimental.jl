```
@spawnat thrdid expr
```

Similar to `StableTasks.@spawn` but creates a **sticky** `Task` and schedules it to run on the thread with the given id (`thrdid`). The task is guaranteed to stay on this thread (it won't migrate to another thread).
