```
assemble_cubicterm(
    mesh::Mesh,
    y::AbstractVector;
    order::Int64 = 3
) -> SparseMatrixCSC{Float64, Int64}
```

標準的な半線形放物方程式の三次項を返します。
