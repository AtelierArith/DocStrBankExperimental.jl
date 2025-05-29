```julia
read_solution(
    problem::TensorInference.ArtifactProblemSpec;
    factor_eltype
) -> Union{Nothing, Float64, Vector}

```

アーティファクト内の解を返します。

UAIファイル形式は次のように定義されています: https://uaicompetition.github.io/uci-2022/file-formats/
