```
result(j::AwsQuantumJob; kwargs...)
```

Download, extract, and deserialize the results of job `j`. Valid `kwargs` are:

  * `poll_timeout_seconds::Int` - the maximum number of seconds to wait while polling for results. Default: 864000
  * `poll_interval_seconds::Int` - how many seconds to wait between download attempts. Default: 5
