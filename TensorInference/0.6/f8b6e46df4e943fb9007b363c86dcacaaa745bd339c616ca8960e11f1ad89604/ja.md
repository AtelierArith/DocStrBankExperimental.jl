```julia
problem_from_artifact(
    artifact_name::String,
    task::String,
    problem_set::String,
    problem_id::Int64
) -> TensorInference.ArtifactProblemSpec

```

アーティファクト名、タスク名、問題セット名、および問題IDからアーティファクトを取得します。
