Tableau for Gauss-Lobatto IIIA-IIIĀ method with s stages

```julia
TableauLobattoIIIAIIIĀ(::Type{T}, s)
TableauLobattoIIIAIIIĀ(s) = TableauLobattoIIIAIIIĀ(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

This [`PartitionedTableau`](@ref) uses [`TableauLobattoIIIA`](@ref) for `a` and [`TableauLobattoIIIĀ`](@ref) for `ā`.
