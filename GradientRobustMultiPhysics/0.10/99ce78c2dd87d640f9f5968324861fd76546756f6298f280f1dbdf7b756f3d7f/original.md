```julia
addblock_matmul!(
    a::GradientRobustMultiPhysics.FEVectorBlock{Tv},
    B::ExtendableSparse.ExtendableSparseMatrix{Tv, Ti<:Integer},
    b::GradientRobustMultiPhysics.FEVectorBlock{Tv};
    factor
)

```

Adds matrix-vector product B times b to FEVectorBlock a.
