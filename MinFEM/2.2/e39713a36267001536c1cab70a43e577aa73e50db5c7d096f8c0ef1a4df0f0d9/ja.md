```
assemble_cubicderivativematrix(
    mesh::Mesh,
    y::AbstractVector;
    order::Int64 = 3
) -> SparseMatrixCSC{Float64, Int64}
```

標準的な半線形楕円方程式の三次項の線形化を返します。
