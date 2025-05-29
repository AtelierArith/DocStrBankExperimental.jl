Tableau for Gauss-Lobatto IIIB-IIIA method with s stages

```julia
TableauLobattoIIIBIIIA(::Type{T}, s)
TableauLobattoIIIBIIIA(s) = TableauLobattoIIIBIIIA(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

This [`PartitionedTableau`](@ref) uses [`TableauLobattoIIIB`](@ref) for `a` and [`TableauLobattoIIIA`](@ref) for `ā`.
