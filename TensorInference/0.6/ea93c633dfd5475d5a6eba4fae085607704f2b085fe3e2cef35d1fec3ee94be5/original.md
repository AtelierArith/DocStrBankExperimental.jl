```julia
struct ArtifactProblemSpec
```

Specify the UAI models from the artifacts. It can be used as the input of [`read_model`](@ref).

### Fields

  * `artifact_path::String`
  * `task::String`
  * `problem_set::String`
  * `problem_id::Int64`
