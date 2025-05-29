```
AwsQuantumTask(device_arn::String, task_spec; kwargs...)
```

Launches an [`AwsQuantumTask`](@ref) based on `task_spec` on the device associated with `device_arn`.

`task_spec` must be one of:

  * `OpenQASMProgram`
  * `BlackbirdProgram`
  * `Problem`
  * `Program`
  * [`Circuit`](@ref)
  * `AHSProgram`
  * [`AnalogHamiltonianSimulation`](@ref)

Valid `kwargs` are:

  * `s3_destination_folder::Tuple{String, String}`, with default value `default_task_bucket()`.
  * `shots::Int` - the number of shots to run, with default value 1000. Value must be between `0` and `MAX_SHOTS` for the specific device.
  * `device_params::Dict{String, Any}` - device specific parameters. Currently only used for DWave devices and simulators.
  * `disable_qubit_rewiring::Bool` - whether to allow qubit rewiring in the compilation stage. Default is `false`.
  * `poll_timeout_seconds::Int` - maximum number of seconds to wait while polling for results. Default: 432000
  * `poll_interval_seconds::Int` - default number of seconds to wait between attempts while polling for results. Default: 1
  * `tags::Dict{String, String}` - tags for the `AwsQuantumTask`
  * `inputs::Dict{String, Float64}` - input values for any free parameters in the `task_spec`
