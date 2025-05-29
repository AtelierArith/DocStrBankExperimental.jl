```
metadata(j::AwsQuantumJob, ::Val{true})
metadata(j::AwsQuantumJob, ::Val{false})
metadata(j::AwsQuantumJob)
```

Fetch metadata for job `j`. If the second argument is `::Val{true}`, use previously cached metadata, if available, otherwise fetch it from the Braket service. If the second argument is `::Val{false}` (default), do not use previously cached metadata, and fetch fresh metadata from the Braket service.
