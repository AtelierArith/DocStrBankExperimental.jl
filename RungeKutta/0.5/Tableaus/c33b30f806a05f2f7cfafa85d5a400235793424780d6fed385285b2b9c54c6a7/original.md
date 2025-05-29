Lobatto IIIB̄ tableau with s stages

```julia
TableauLobattoIIIB̄(::Type{T}, s)
TableauLobattoIIIB̄(s) = TableauLobattoIIIB̄(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

Lobatto IIIB̄ tableau is the conjugate symplectic to [`TableauLobattoIIIB`](@ref). On paper, its coefficients are identical to [`TableauLobattoIIIA`](@ref), however, they are computed by the symplecticity condition and not by the formula for Lobatto IIIA and thus the numerical values are slightly different.
