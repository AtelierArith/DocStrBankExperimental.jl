```
log_events(log_group, log_stream) -> Union{Vector{LogEvent}, Nothing}
```

Fetches the CloudWatch log from the specified log group and stream as a `Vector` of `LogEvent`s. If the log stream does not exist then `nothing` will be returned.
