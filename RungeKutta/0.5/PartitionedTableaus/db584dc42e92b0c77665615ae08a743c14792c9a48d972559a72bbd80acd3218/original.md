Tableau for Gauss-Lobatto IIIC̄-IIIC method with s stages

```julia
TableauLobattoIIIC̄IIIC(::Type{T}, s)
TableauLobattoIIIC̄IIIC(s) = TableauLobattoIIIC̄IIIC(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

This [`PartitionedTableau`](@ref) uses [`TableauLobattoIIIC̄`](@ref) for `a` and [`TableauLobattoIIIC`](@ref) for `ā`.
