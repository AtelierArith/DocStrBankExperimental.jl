Tableau for Gauss-Lobatto IIID-IIID̄ method with s stages

```julia
TableauLobattoIIIDIIID̄(::Type{T}, s)
TableauLobattoIIIDIIID̄(s) = TableauLobattoIIIDIIID̄(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

This [`PartitionedTableau`](@ref) uses [`TableauLobattoIIID`](@ref) for `a` and [`TableauLobattoIIID̄`](@ref) for `ā`.
