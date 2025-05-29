```julia
dataset_from_artifact(
    artifact_name::AbstractString
) -> Dict{String, Dict{String, Dict{Int64, TensorInference.ArtifactProblemSpec}}}

```

Helper function that captures the problem names that belong to `problem_set` for the given task.
