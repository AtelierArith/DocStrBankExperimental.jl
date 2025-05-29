```
assemble_dirichletcondition_rhs!(
    A::SparseMatrixCSC{Float64, Int64},
    rhs::AbstractVector{Float64},
    DI::Set{Int64},
    bc::AbstractVector{Float64};
    qdim::Int64 = 1
)
```

Modify a right hand side according to the given Dirichlet conditions. Behaviour is similar to `assemble_dirichletcondition!(...)` however the system matrix A is not updated. Can be relevant for iterative algorithm, where the system matrix is constant and only the right hand side changes. Then one can store the modified matrix and only assemble the right hand side in every iteration.

DI has to be the set of node indices for which the condition should be active. For vector valued states either DI can be set to each component that should have a Dirichlet condtion or qdim is set, if all components should have the condition.
