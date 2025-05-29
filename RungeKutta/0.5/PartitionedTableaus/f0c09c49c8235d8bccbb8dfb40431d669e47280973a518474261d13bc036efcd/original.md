Tableau for Gauss-Lobatto IIIE-IIIĒ method with s stages

```julia
TableauLobattoIIIEIIIĒ(::Type{T}, s)
TableauLobattoIIIEIIIĒ(s) = TableauLobattoIIIEIIIĒ(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

This [`PartitionedTableau`](@ref) uses [`TableauLobattoIIIE`](@ref) for `a` and [`TableauLobattoIIIĒ`](@ref) for `ā`.
