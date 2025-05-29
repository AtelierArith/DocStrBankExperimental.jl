```
result(t::AwsQuantumTask)
```

Fetches the result of task `t`, if available. Blocks until a result is available, in which case the result is returned, or the task enters a terminal state without a result (`"FAILED"` or `"CANCELLED"`) or exceeds its its polling timeout (set at task creation), in which case `nothing` is returned.
