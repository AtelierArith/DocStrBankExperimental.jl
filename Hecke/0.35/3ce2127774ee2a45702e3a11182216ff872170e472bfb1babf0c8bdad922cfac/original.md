```
+(P::EllipticCurvePoint, Q::EllipticCurvePoint) -> EllipticCurvePoint
```

Add two points on an elliptic curve.

# Examples

```jldoctest
julia> E = elliptic_curve(QQ, [1, 2]);

julia> P = E([1, -2]);

julia> P + P
(-1 : 0 : 1)
```
