```
assemble_dirichletcondition_rhs!(
    A::SparseMatrixCSC{Float64, Int64},
    rhs::AbstractVector{Float64},
    DI::Set{Boundary},
    bc::AbstractVector{Float64};
    qdim::Int64 = 1
)
```

前の `assemble_dirichletcondition_rhs!(...)` と同様ですが、Dirichlet ノードの引数として `Set{Int64}` の代わりに `Set{Boundary}` を取ります。したがって、最初にノードを抽出し、それを基本関数に渡します。
