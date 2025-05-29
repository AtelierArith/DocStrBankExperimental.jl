```
parent(P::EllipticCurvePoint) -> EllipticCurve
```

Return the elliptic curve on which $P$ lies.

# Examples

```jldoctest
julia> E = elliptic_curve(QQ, [1, 2]);

julia> P = E([1, -2]);

julia> E == parent(P)
true
```
