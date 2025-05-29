```
elliptic_curve(f::PolyRingElem, [h::PolyRingElem,] check::Bool = true) -> EllipticCurve
```

Return the elliptic curve $y^2 + h(x)y = f(x)$ respectively $y^2 + y = f(x)$, if no $h$ is specified. The polynomial $f$ must be monic of degree 3 and $h$ of degree at most 1.

Per default, it is checked whether the discriminant is non-zero. This can be disabled by setting `check = false`.

# Examples

```jldoctest
julia> Qx, x = QQ["x"];

julia> elliptic_curve(x^3 + x + 1)
Elliptic curve
  over rational field
with equation
  y^2 = x^3 + x + 1

julia> elliptic_curve(x^3 + x + 1, x)
Elliptic curve
  over rational field
with equation
  y^2 + x*y = x^3 + x + 1
```
