```
download_result(j::AwsQuantumJob; kwargs...)
```

Download and extract the results of job `j`. Valid `kwargs` are:

  * `extract_to::String` - the local folder to extract the results to. Default is the current working directory.
  * `poll_timeout_seconds::Int` - the maximum number of seconds to wait while polling for results. Default: 864000
  * `poll_interval_seconds::Int` - how many seconds to wait between download attempts. Default: 5
