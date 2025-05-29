Tableau for Gauss-Lobatto IIIG-IIIḠ method with s stages

```julia
TableauLobattoIIIGIIIḠ(::Type{T}, s)
TableauLobattoIIIGIIIḠ(s) = TableauLobattoIIIGIIIḠ(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

This [`PartitionedTableau`](@ref) uses [`TableauLobattoIIIG`](@ref) for `a` and [`TableauLobattoIIIḠ`](@ref) for `ā`.
