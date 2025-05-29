```
rmproc(vm[; session=AzSession(;lazy=true), verbose=0, nretry=10])
```

Delete the VM that was created using the `addproc` method.

# Parameters

  * `session=AzSession(;lazy=true)` Azure session for OAuth2 authentication
  * `verbose=0` verbosity flag passed to HTTP.jl methods
  * `nretry=10` max number of retries for retryable REST calls
  * `show_quota=false` after various operation, show the "x-ms-rate-remaining-resource" response header.  Useful for debugging/understanding Azure quota's.
