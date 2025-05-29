Lobatto IIIC̄ tableau with s stages

```julia
TableauLobattoIIIC̄(::Type{T}, s)
TableauLobattoIIIC̄(s) = TableauLobattoIIIC̄(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

Lobatto IIIC̄ tableau is the conjugate symplectic to [`TableauLobattoIIIC`](@ref). On paper, its coefficients are identical to [`TableauLobattoIII`](@ref), however, they are computed by the symplecticity condition and not by the formula for Lobatto III and thus the numerical values are slightly different.
