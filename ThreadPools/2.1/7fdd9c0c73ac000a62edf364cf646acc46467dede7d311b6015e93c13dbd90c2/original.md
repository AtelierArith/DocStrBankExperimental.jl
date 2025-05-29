```
Base.put!(pool::LoggedQueuePool, t::Task)
```

Put the task `t` into the pool, blocking until the pool has an available thread.
