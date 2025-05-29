```
results(b::AwsQuantumTaskBatch; kwargs)
```

Valid `kwargs` are:

  * `fail_unsuccessful::Bool` - whether to throw an error if any tasks in the batch are unsuccessful after retries. Default: `false`
  * `max_retries::Int` - maximum number of times to retry a failed task. Default: 3
  * `use_cached_value::Bool` - whether to reuse previously downloaded results for tasks or download all results fresh. Default: `true`

Blocks and waits while retrieving results for every task in `b`.
