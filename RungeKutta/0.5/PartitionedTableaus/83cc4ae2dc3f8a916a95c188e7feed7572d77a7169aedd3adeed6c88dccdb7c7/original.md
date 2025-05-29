Partitioned Gauss-Lobatto IIIA-IIIB tableau with s stages

```julia
TableauLobattoIIIAIIIB(::Type{T}, s)
TableauLobattoIIIAIIIB(s) = TableauLobattoIIIAIIIB(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

This [`PartitionedTableau`](@ref) uses [`TableauLobattoIIIA`](@ref) for `a` and [`TableauLobattoIIIB`](@ref) for `ā`.
