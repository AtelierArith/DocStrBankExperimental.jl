```
assemble_massmatrix(
    mesh::Mesh;
    qdim::Int64 = 1,
    order::Int64 = 1
) -> SparseMatrixCSC{Float64, Int64}
```

メッシュのすべての要素と qdim コンポーネントに対して、指定された局所積分次数の質量行列を返します。
