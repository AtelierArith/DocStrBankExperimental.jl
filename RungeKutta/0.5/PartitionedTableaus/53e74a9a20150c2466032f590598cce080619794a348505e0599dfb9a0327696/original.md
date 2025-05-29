Tableau for Gauss-Lobatto IIIF̄-IIIF method with s stages

```julia
TableauLobattoIIIF̄IIIF(::Type{T}, s)
TableauLobattoIIIF̄IIIF(s) = TableauLobattoIIIF̄IIIF(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

This [`PartitionedTableau`](@ref) uses [`TableauLobattoIIIF̄`](@ref) for `a` and [`TableauLobattoIIIF`](@ref) for `ā`.
