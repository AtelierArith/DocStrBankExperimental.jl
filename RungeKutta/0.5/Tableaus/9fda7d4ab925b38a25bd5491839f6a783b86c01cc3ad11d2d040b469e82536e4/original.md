Lobatto IIIĀ tableau with s stages

```julia
TableauLobattoIIIĀ(::Type{T}, s)
TableauLobattoIIIĀ(s) = TableauLobattoIIIĀ(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

Lobatto IIIĀ tableau is the conjugate symplectic to [`TableauLobattoIIIA`](@ref). On paper, its coefficients are identical to [`TableauLobattoIIIB`](@ref), however, they are computed by the symplecticity condition and not by the formula for Lobatto IIIB and thus the numerical values are slightly different.
