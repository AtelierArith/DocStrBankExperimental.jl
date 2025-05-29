```julia
struct ArtifactProblemSpec
```

アーティファクトからのUAIモデルを指定します。これは[`read_model`](@ref)の入力として使用できます。

### フィールド

  * `artifact_path::String`
  * `task::String`
  * `problem_set::String`
  * `problem_id::Int64`
