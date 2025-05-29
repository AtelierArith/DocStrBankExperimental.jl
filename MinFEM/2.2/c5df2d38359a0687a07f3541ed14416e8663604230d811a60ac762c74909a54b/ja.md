```julia
jacobian(
    mesh::MinFEM.Mesh,
    element::Int64
) -> Tuple{Float64, LinearAlgebra.Adjoint{Float64, Matrix{Float64}}}

```

前の `jacobian(...)` と同様ですが、メッシュと要素IDを引数として受け取ります。メッシュからサポートノードの座標を抽出し、それを基本関数に渡します。
