```
logs(j::AwsQuantumJob; wait::Bool=false, poll_interval_seconds::Int=5)
```

Fetches the logs of job `j`. If `wait` is `true`, blocks until `j` has entered a terminal state (`"COMPLETED"`, `"FAILED"`, or `"CANCELLED"`). Polls every `poll_interval_seconds` for new log data.
