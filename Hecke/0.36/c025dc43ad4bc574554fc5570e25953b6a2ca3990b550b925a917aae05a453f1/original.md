```
division_points(P::EllipticCurvePoint, m::Int) -> EllipticCurvePoint
```

Compute the set of points $Q$ defined over the base field such that $mQ = P$. Returns the empty list if no such points exist.

# Examples

```jldoctest
julia> E = elliptic_curve(QQ, [1, 2]);

julia> division_points(infinity(E), 2)
2-element Vector{EllipticCurvePoint{QQFieldElem}}:
 (0 : 1 : 0)
 (-1 : 0 : 1)
```
