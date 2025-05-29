Tableau for Gauss-Lobatto IIIB-IIIB̄ method with s stages

```julia
TableauLobattoIIIBIIIB̄(::Type{T}, s)
TableauLobattoIIIBIIIB̄(s) = TableauLobattoIIIBIIIB̄(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

This [`PartitionedTableau`](@ref) uses [`TableauLobattoIIIB`](@ref) for `a` and [`TableauLobattoIIIB̄`](@ref) for `ā`.
