```julia
jacobian_boundary(
    coords::Vector{Vector{Float64}}
) -> Union{Nothing, Float64, Int64}

```

与えられた座標でスパンされたFEM境界要素（d-1次元）のヤコビ行列の行列式（すなわち要素の重み）を返します。

一般的に、座標はメッシュ内の要素に対応しますが、必ずしもそうである必要はありません。
