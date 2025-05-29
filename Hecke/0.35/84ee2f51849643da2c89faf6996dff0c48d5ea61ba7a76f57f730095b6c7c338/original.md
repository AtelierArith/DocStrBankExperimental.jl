```
elliptic_curve([K::Field], x::Vector; check::Bool = true) -> EllipticCurve
```

Construct an elliptic curve with Weierstrass equation specified by the coefficients in `x`, which must have either length 2 or 5.

Per default, it is checked whether the discriminant is non-zero. This can be disabled by setting `check = false`.

# Examples

```jldoctest
julia> elliptic_curve(QQ, [1, 2, 3, 4, 5])
Elliptic curve
  over rational field
with equation
  y^2 + x*y + 3*y = x^3 + 2*x^2 + 4*x + 5

julia> elliptic_curve(GF(3), [1, 1])
Elliptic curve
  over prime field of characteristic 3
with equation
  y^2 = x^3 + x + 1
```
