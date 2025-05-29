```julia
jacobian(
    coords::Vector{Vector{Float64}}
) -> Tuple{Float64, LinearAlgebra.Adjoint{Float64, Matrix{Float64}}}

```

与えられた座標でスパンされたFEM要素のヤコビアンの行列式（すなわち要素の重み）と逆転置を返します。

一般的に、座標はメッシュ内の1つの要素に対応しますが、必ずしもそうである必要はありません。
