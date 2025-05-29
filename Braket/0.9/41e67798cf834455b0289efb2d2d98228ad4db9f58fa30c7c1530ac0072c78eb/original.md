```
@hybrid_job [device] [job_creation_kwargs] job_function(args...; kwargs..)
```

Run `job_function` inside an [Amazon Braket Job](https://docs.aws.amazon.com/braket/latest/developerguide/braket-jobs.html), launching the job with creation arguments defined by `job_creation_kwargs`, and reserving device `device` (may be empty, in which case `local:local/none` is used). `device` should be either a [valid AWS device ARN](https://docs.aws.amazon.com/braket/latest/developerguide/braket-devices.html) or use the format `local:<simulator_provider>/<simulator_name>` (see the developer guide on [embedded simulators](https://docs.aws.amazon.com/braket/latest/developerguide/pennylane-embedded-simulators.html)).

Valid job creation keyword arguments are:     - `jl_dependencies::String`: a path to a `Project.toml` containing the Julia packages needed to run `job_function`. Can be `""` (default).     - `py_dependencies::String`: a path to a `requirements.txt` containing the Python packages needed to run `job_function`. Can be `""` (default).     - `as_local::Bool`: whether to run the job in [local mode](https://docs.aws.amazon.com/braket/latest/developerguide/braket-jobs-local-mode.html). Default is `false`, running as a Hybrid, non-local Job.     - `include_modules`: unused but reserved argument.     - `using_jl_pkgs::Union{String, Vector{String}}`: Julia packages to load with `using [pkgs]` before the `job_function` is called within the job.     - `include_jl_files::Union{String, Vector{String}}`: path(s) to Julia file(s) to load with `include(file)` before `job_function` is called within the job.     - creation arguments for [`AwsQuantumJob`](@ref)

Currently, `args` and `kwargs` to `job_function` must be serializable by `JLD2.jl`. `job_function` must be a Julia function, not Python.

!!! note
    The paths to include files and dependencies are resolved from the *call location* of this macro - to ensure your paths will resolve correctly, use absolute, not relative, paths.


# Examples

```julia
function my_job_func(a, b::Int; c=0, d::Float64=1.0, kwargs...)
    Braket.save_job_result(job_helper())
    py_reqs = read(joinpath(Braket.get_input_data_dir(), "requirements.txt"), String)
    hyperparameters = Braket.get_hyperparameters()
    write("test/output_file.txt", "hello")
    return 0
end

py_deps = joinpath(@__DIR__, "requirements.txt")
jl_deps = joinpath(@__DIR__, "JobProject.toml")
input_data = joinpath(@__DIR__, "requirements")
include_jl_files = joinpath(@__DIR__, "job_test_script.jl")

j = @hybrid_job Braket.SV1() wait_until_complete=true as_local=false include_modules="job_test_script" using_jl_pkgs="LinearAlgebra" include_jl_files=include_jl_files py_dependencies=py_deps jl_dependencies=jl_deps input_data=input_data my_job_func(MyStruct(), 2, d=5.0, extra_kwarg="extra_value")
```
