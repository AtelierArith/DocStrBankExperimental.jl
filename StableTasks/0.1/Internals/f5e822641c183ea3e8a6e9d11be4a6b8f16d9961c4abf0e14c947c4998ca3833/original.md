```
@spawn [:default|:interactive] expr
```

Similar to `Threads.@spawn` but type-stable. Creates a `Task` and schedules it to run on any available thread in the specified threadpool (defaults to the `:default` threadpool).
