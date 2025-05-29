```
elliptic_curve_from_j_invariant(j::FieldElem) -> EllipticCurve
```

Return an elliptic curve with the given $j$-invariant.

# Examples

```jldoctest
julia> K = GF(3)
Prime field of characteristic 3

julia> elliptic_curve_from_j_invariant(K(2))
Elliptic curve
  over prime field of characteristic 3
with equation
  y^2 + x*y = x^3 + 1
```
