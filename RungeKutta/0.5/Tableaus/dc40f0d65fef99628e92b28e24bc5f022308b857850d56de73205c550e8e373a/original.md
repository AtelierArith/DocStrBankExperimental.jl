Lobatto IIIF̄ tableau with s stages

```julia
TableauLobattoIIIF̄(::Type{T}, s)
TableauLobattoIIIF̄(s) = TableauLobattoIIIF̄(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

The Lobatto IIIF̄ tableau is the conjugate symplectic to [`TableauLobattoIIIF`](@ref).
