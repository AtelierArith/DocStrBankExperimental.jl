```
equation([R::MPolyRing,] E::EllipticCurve) -> MPolyRingElem
```

Return the equation defining the elliptic curve $E$ as a bivariate polynomial. If the polynomial ring $R$ is specified, it must by a bivariate polynomial ring.

# Examples

```jldoctest
julia> E = elliptic_curve(QQ, [1, 2, 3, 4, 5]);

julia> equation(E)
-x^3 - 2*x^2 + x*y - 4*x + y^2 + 3*y - 5
```
