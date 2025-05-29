```julia
read_solution(
    problem::TensorInference.ArtifactProblemSpec;
    factor_eltype
) -> Union{Nothing, Float64, Vector}

```

Return the solution in the artifact.

The UAI file formats are defined in: https://uaicompetition.github.io/uci-2022/file-formats/
