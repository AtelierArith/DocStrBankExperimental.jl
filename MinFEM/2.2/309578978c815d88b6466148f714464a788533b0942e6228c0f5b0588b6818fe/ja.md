```
assemble_cubicsecondderivativematrix(
    mesh::Mesh,
    y::AbstractVector,
    p::AbstractVector;
    order::Int64 = 3
) -> SparseMatrixCSC{Float64, Int64}
```

標準的な半線形楕円方程式の状態 y の周りの三次項の二次導関数を返します。
