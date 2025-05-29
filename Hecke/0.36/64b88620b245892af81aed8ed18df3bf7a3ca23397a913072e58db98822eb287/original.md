```
hyperelliptic_polynomials([R::PolyRing,] E::EllipticCurve) -> PolyRingElem, PolyRingElem
```

Return univariate polynomials $f, h$ such that $E$ is given by $y^2 + h*y = f$.

# Examples

```jldoctest
julia> E = elliptic_curve(QQ, [1, 2, 3, 4, 5]);

julia> hyperelliptic_polynomials(E)
(x^3 + 2*x^2 + 4*x + 5, x + 3)
```
