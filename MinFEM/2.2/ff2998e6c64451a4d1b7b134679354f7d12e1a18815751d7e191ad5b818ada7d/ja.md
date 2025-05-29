```julia
assemble_elasticity(
    mesh::MinFEM.Mesh,
    lambda::Float64,
    mu::Float64
) -> SparseArrays.SparseMatrixCSC{Float64, Int64}

```

メッシュのすべての要素と画像次元 qdim に対して、定数係数 λ と μ を持つ線形弾性剛性行列を返します。
