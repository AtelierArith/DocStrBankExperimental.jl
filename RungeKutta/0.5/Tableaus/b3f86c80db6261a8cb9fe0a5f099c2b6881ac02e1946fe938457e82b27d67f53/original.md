Lobatto IIIḠ tableau with s stages

```julia
TableauLobattoIIIḠ(::Type{T}, s)
TableauLobattoIIIḠ(s) = TableauLobattoIIIḠ(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

Lobatto IIIḠ tableau is the conjugate symplectic to [`TableauLobattoIIIG`](@ref). On paper, the coefficients of the Lobatto IIIG tableau are symplectic, however, the Lobatto IIIḠ coefficients are computed by the symplecticity condition and not by the formula for Lobatto IIIG and thus the numerical values are slightly different.
