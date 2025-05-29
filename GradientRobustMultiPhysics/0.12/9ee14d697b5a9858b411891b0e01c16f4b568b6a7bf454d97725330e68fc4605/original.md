```julia
FESpaces(
    FEV::GradientRobustMultiPhysics.FEVector{T, Tv, Ti}
) -> Vector{T} where T<:(GradientRobustMultiPhysics.FESpace{_A, _B} where {_B, _A})

```

Returns the vector of FEspaces for the blocks of the given FEVector.
