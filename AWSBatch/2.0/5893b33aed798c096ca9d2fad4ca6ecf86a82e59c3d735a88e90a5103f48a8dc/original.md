```
log_events(job::BatchJob) -> Union{Vector{LogEvent}, Nothing}
```

Fetches the logStreamName, fetches the CloudWatch logs, and returns a vector of log events. If the log stream does not currently exist then `nothing` is returned.

NOTES:

  * The `logStreamName` isn't available until the job is RUNNING, so you may want to use `wait(job)` or `wait(job, [AWSBatch.SUCCEEDED])` prior to calling this function.
