```
run_batch(;
    name::AbstractString="",
    queue::AbstractString="",
    region::AbstractString="",
    definition::Union{AbstractString, JobDefinition, Nothing}=nothing,
    image::AbstractString="",
    vcpus::Integer=1,
    memory::Integer=-1,
    role::AbstractString="",
    cmd::Cmd=``,
    num_jobs::Integer=1,
    parameters::Dict{String, String}=Dict{String, String}(),
) -> BatchJob
```

Handles submitting a BatchJob based on various potential defaults. For example, default job fields can be inferred from an existing job definition or an existing job (if currently running in a batch job).

Order of priority from highest to lowest:

1. Explict arguments passed in via `kwargs`.
2. Inferred environment (e.g., `AWS_BATCH_JOB_ID` environment variable set)
3. Job definition parameters

If no valid job definition exists (see [`AWSBatch.job_definition_arn`](@ref) then a new job definition will be created and registered based on the job parameters.
