```
assemble_basismatrix(
    mesh::Mesh;
    qdim::Int64 = 1,
    order::Int64 = 3
) -> SparseMatrixCSC{Float64, Int64}
```

与えられたローカル積分次数に対する離散基底行列を、メッシュのすべての要素とqdim成分に対して返します。
