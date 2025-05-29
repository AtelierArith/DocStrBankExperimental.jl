```
state(j::AwsQuantumJob, ::Val{true})
state(j::AwsQuantumJob, ::Val{false})
state(j::AwsQuantumJob)
```

Fetch the state for job `j`. Possible states are `"CANCELLED"`, `"FAILED"`, `"COMPLETED"`, `"QUEUED"`, and `"RUNNING"`. If the second argument is `::Val{true}`, use previously cached metadata, if available, otherwise fetch it from the Braket service. If the second argument is `::Val{false}` (default), do not use previously cached metadata, and fetch fresh metadata from the Braket service.
