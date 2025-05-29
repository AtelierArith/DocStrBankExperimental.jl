```
execute!(job::AbstractJob, exec::Executor)
```

Execute a given `AbstractJob` associated with the `Executor`.

This function checks if the `job` has succeeded. If so, it stops immediately. If not, it sleeps for a `exec.delay`, then runs the `job`. If `exec.maxattempts` is more than $1$, it loops over the remaining attempts, sleeping for an `exec.interval`, running the `job`, and waiting in each loop.
