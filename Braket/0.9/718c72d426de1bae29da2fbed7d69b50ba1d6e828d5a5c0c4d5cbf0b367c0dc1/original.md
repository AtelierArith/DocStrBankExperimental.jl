```
LocalQuantumJob(device::Union{String, BraketDevice}, source_module::String; kwargs...)
```

Create and launch a `LocalQuantumJob` which will use device `device` (a managed simulator, a QPU, or an [embedded simulator](https://docs.aws.amazon.com/braket/latest/developerguide/pennylane-embedded-simulators.html)) and will run the code (either a single file, or a Julia package, or a Python module) located at `source_module`. `device` can be either the device's ARN as a `String`, or a [`BraketDevice`](@ref).  A *local* job runs *locally* on your computational resource by launching the Job container locally using `docker`. The job will block until it completes, replicating the `wait_until_complete` behavior of [`AwsQuantumJob`](@ref).

The keyword arguments `kwargs` control the launch configuration of the job.

# Keyword Arguments

  * `entry_point::String` - the function to run in `source_module` if `source_module` is a Python module/Julia package. Defaults to an empty string, in which case the behavior depends on the code language. In Python, the job will attempt to find a function called `main` in `source_module` and run it. In Julia, `source_module` will be loaded and run with Julia's [`include`](https://docs.julialang.org/en/v1/base/base/#Base.include).
  * `image_uri::String` - the URI of the Docker image in ECR to run the Job on. Defaults to an empty string, in which case the [base container](https://docs.aws.amazon.com/braket/latest/developerguide/braket-jobs-script-environment.html) is used.
  * `job_name::String` - the name for the job, which will be displayed in the [jobs console](https://docs.aws.amazon.com/braket/latest/developerguide/braket-jobs-first.html). The default is a combination of the container image name and the current time.
  * `code_location::String` - the S3 prefix URI to which code will be uploaded. The default is `default_bucket()/jobs/<job_name>/script`
  * `role_arn::String` - not used for `LocalQuantumJob`s.
  * `hyperparameters::Dict{String, Any}` - hyperparameters to provide to the job which will be available from an environment variable when the job is run. See the [Amazon Braket documentation](https://docs.aws.amazon.com/braket/latest/developerguide/braket-jobs-hyperparameters.html) for more.
  * `input_data::Union{String, Dict}` - information about the training/input data to provide to the job. A `Dict` should map channel names to local paths or S3 URIs. Contents found at any local paths encoded as `String`s will be uploaded to S3 at `s3://{default_bucket_name}/jobs/{job_name}/data/{channel_name}`. If a local path or S3 URI is provided, it will be given a default channel name `"input"`. The default is `Dict()`.
  * `instance_config::InstanceConfig` - not used for `LocalQuantumJob`s.
  * `distribution::String` - not used for `LocalQuantumJob`s.
  * `stopping_condition::StoppingCondition` - the maximum length of time, in seconds, that a job can run before being forcefully stopped. The default is `StoppingCondition(5 * 24 * 60 * 60)`.
  * `output_data_config::OutputDataConfig` - specifies the location for the output of the job. Any data stored here will be available to [`download_result`](@ref) and [`results`](@ref). The default is `OutputDataConfig("s3://{default_bucket_name}/jobs/{job_name}/data")`.
  * `copy_checkpoints_from_job::String` - specifies the job ARN whose checkpoint is to be used in the current job. Specifying this value will copy over the checkpoint data from `use_checkpoints_from_job`'s `checkpoint_config` S3 URI to the current job's `checkpoint_config` S3 URI, making it available at `checkpoint_config.localPath` during the job execution. The default is not to copy any checkpoints (an empty string).
  * `checkpoint_config::CheckpointConfig` - specifies the location where checkpoint data for *this* job is to be stored. The default is `CheckpointConfig("/opt/jobs/checkpoints", "s3://{default_bucket_name}/jobs/{job_name}/checkpoints")`.
  * `tags::Dict{String, String}` - specifies the key-value pairs for tagging this job.
