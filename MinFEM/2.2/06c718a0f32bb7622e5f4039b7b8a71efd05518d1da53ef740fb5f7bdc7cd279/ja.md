```julia
jacobian(
    mesh::MinFEM.Mesh,
    nodes::Vector{Int64}
) -> Tuple{Float64, LinearAlgebra.Adjoint{Float64, Matrix{Float64}}}

```

前の `jacobian(...)` と同様ですが、メッシュとノードのセットを引数として取ります。メッシュから座標を抽出し、それを基本関数に渡します。

一般的に、座標はメッシュ内の1つの要素に対応しますが、必ずしもそうである必要はありません。
