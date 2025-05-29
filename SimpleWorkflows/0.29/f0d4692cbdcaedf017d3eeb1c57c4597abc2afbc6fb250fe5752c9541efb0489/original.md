```
execute!(workflow::AbstractWorkflow, exec::Executor)
```

Executes the jobs from the workflow of the provided Executor instance.

The function will attempt to execute all the jobs up to `exec.maxattempts` times. If all jobs have succeeded, the function will stop immediately. Otherwise, it will wait for a duration equal to `exec.interval` before the next attempt.
