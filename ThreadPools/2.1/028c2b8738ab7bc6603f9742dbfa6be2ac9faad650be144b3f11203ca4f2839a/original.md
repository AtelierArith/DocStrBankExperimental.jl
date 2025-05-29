```
Base.put!(pool::LoggedQueuePool, fn, args...)
Base.put!(fn, pool::LoggedQueuePool, args...)
```

Creates a task that runs `fn(args...)` and adds it to the pool, blocking  until the pool has an available thread.
