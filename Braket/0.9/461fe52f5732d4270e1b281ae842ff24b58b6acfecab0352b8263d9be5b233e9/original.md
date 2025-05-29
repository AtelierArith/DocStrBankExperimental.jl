```
metadata(t::AwsQuantumTask, ::Val{false})
metadata(t::AwsQuantumTask, ::Val{true})
```

Fetch metadata for task `t`. If the second argument is `::Val{true}`, use previously cached metadata, if available, otherwise fetch it from the Braket service. If the second argument is `::Val{false}` (default), do not use previously cached metadata, and fetch fresh metadata from the Braket service.
