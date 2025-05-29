Tableau for Gauss-Lobatto IIIF-IIIF̄ method with s stages

```julia
TableauLobattoIIIFIIIF̄(::Type{T}, s)
TableauLobattoIIIFIIIF̄(s) = TableauLobattoIIIFIIIF̄(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

This [`PartitionedTableau`](@ref) uses [`TableauLobattoIIIF`](@ref) for `a` and [`TableauLobattoIIIF̄`](@ref) for `ā`.
