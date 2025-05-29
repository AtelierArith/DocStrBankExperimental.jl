```julia
dataset_from_artifact(
    artifact_name::AbstractString
) -> Dict{String, Dict{String, Dict{Int64, TensorInference.ArtifactProblemSpec}}}

```

与えられたタスクに対して `problem_set` に属する問題名をキャプチャするヘルパー関数です。
