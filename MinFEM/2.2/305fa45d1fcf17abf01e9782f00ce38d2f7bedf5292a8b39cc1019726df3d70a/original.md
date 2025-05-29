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

Same as previous `assemble_dirichletcondition!(...)`, but takes `Set{Boundary}` instead of `Set{Int64}` as argument for the Dirichlet nodes. Thus extracts the nodes first and then passes them to the base function.
