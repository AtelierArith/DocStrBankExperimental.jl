```
AwsQuantumTaskBatch(device_arn::String, task_specs::Vector{<:Union{AbstractProgram, Circuit}}; kwargs...) -> AwsQuantumTaskBatch
```

Launches a batch of concurrent tasks specified by `task_specs` on `device_arn`.

Valid `kwargs` are:

  * `s3_destination_folder::Tuple{String, String}` - s3 bucket and prefix in which to store results. Default: `default_task_bucket()`
  * `shots::Int` - the number of shots to run each task with. Default: 1000
  * `poll_timeout_seconds::Int` - maximum number of seconds to wait while polling for results. Default: 432000
  * `poll_interval_seconds::Int` - default number of seconds to wait between attempts while polling for results. Default: 1
