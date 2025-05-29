Lobatto IIIĒ tableau with s stages

```julia
TableauLobattoIIIĒ(::Type{T}, s)
TableauLobattoIIIĒ(s) = TableauLobattoIIIĒ(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

Lobatto IIIĒ tableau is the conjugate symplectic to [`TableauLobattoIIIE`](@ref). On paper, the coefficients of the Lobatto IIIE tableau are symplectic, however, the Lobatto IIIĒ coefficients are computed by the symplecticity condition and not by the formula for Lobatto IIIE and thus the numerical values are slightly different.
