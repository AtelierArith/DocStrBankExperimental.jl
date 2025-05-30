```julia
default_weight_matrix(
    mode::MomentMatching.EstimationMode,
    typemom::String,
    n::Integer
) -> Matrix{Float64}

```

目的関数を計算するためのデフォルトの重み行列を設定します。これは、[`EstimationMode`](@ref) の任意のサブタイプに対して定義されるべきであり、そうでなければ単位行列を返します。
