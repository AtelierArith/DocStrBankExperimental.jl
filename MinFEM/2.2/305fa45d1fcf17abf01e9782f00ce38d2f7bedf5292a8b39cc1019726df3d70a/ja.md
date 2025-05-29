```
assemble_dirichletcondition!(
    A::SparseMatrixCSC{Float64, Int64},
    DI::Set{Boundary};
    rhs = [],
    bc = [],
    qdim::Int64 = 1,
    insert = 1.0
)
```

前の `assemble_dirichletcondition!(...)` と同様ですが、Dirichlet ノードの引数として `Set{Int64}` の代わりに `Set{Boundary}` を取ります。したがって、最初にノードを抽出し、それを基本関数に渡します。
