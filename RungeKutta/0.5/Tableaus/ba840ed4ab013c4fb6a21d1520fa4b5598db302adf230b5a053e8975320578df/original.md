Lobatto IIID̄ tableau with s stages

```julia
TableauLobattoIIID̄(::Type{T}, s)
TableauLobattoIIID̄(s) = TableauLobattoIIID̄(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

Lobatto IIID̄ tableau is the conjugate symplectic to [`TableauLobattoIIID`](@ref). On paper, the coefficients of the Lobatto IIID tableau are symplectic, however, the Lobatto IIID̄ coefficients are computed by the symplecticity condition and not by the formula for Lobatto IIID and thus the numerical values are slightly different.
