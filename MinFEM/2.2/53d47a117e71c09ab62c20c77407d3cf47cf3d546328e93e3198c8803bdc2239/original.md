```
assemble_dirichletcondition!(
    A::SparseMatrixCSC{Float64, Int64},
    DI::Set{Int64}; 
    rhs = [],
    bc = [],
    qdim::Int64 = 1,
    insert = 1.0
)
```

Modify a stiffness matrix and a right hand side according to the given Dirichlet conditions.

DI has to be the set of node indices for which the condition should be active. For vector valued states either DI can be set to each component that should have a Dirichlet condtion or qdim is set, if all components should have the condition. If the rhs shall be updated bc needs to be specified explicitly as well. The value insert is put as diagonal element. Usually you want a 1.0 here.
