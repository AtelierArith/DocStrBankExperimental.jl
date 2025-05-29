Tableau for Gauss-Lobatto IIIC-IIIC̄ method with s stages

```julia
TableauLobattoIIICIIIC̄(::Type{T}, s)
TableauLobattoIIICIIIC̄(s) = TableauLobattoIIICIIIC̄(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

This [`PartitionedTableau`](@ref) uses [`TableauLobattoIIIC`](@ref) for `a` and [`TableauLobattoIIIC̄`](@ref) for `ā`.
