```
onworker(
    f::Function, args...;
    pool::AbstractWorkerPool = ppt_worker_pool(),
    maxtime::Real = 0, tries::Integer = 1, label::AbstractString = ""
)
```

Runs `f(args...)` on an available worker process from the given `pool` and returns the result.

If `maxtime > 0`, a maximum time for the activity is set. If the activity takes longer than `maxtime` seconds, the process running it (if not the main process) will be terminated.

`label` is used for debug-logging.

If a problem occurs (maxtime or worker failure) while running the activity, reschedules the task if the maximum number of tries has not yet been reached, otherwise throws an exception.
