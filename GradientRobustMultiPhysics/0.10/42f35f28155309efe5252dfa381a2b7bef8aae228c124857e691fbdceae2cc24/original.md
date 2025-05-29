```julia
append!(
    FEF::GradientRobustMultiPhysics.FEVector{T},
    name::String,
    FES::GradientRobustMultiPhysics.FESpace{Tv, Ti, FEType, APT}
)

```

Custom `append` function for `FEVector` that adds a FEVectorBlock at the end.
