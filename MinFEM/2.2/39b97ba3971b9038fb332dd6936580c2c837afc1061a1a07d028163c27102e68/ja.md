```julia
quadrature_weights_boundary(
    d::Int64,
    order::Int64
) -> Union{Nothing, Vector{Float64}}

```

与えられた次数までの多項式の正確な積分のための(d-1)次元FEM基準要素上のガウス・レジャンドル積分点の重みを返します。
