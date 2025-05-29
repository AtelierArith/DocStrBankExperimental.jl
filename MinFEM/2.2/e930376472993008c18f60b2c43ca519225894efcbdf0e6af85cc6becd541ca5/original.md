```
assemble_dirichletcondition_rhs!(
    A::SparseMatrixCSC{Float64, Int64},
    rhs::AbstractVector{Float64},
    DI::Set{Boundary},
    bc::AbstractVector{Float64};
    qdim::Int64 = 1
)
```

Same as previous `assemble_dirichletcondition_rhs!(...)`, but takes `Set{Boundary}` instead of `Set{Int64}` as argument for the Dirichlet nodes. Thus extracts the nodes first and then passes them to the base function.
