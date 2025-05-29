```
is_on_curve(E::EllipticCurve, coords::Vector) -> Bool
```

Return true if `coords` defines a point on $E$ and false otherwise. The array `coords` must have length 2.

# Examples

```jldoctest
julia> E = elliptic_curve(QQ, [1, 2]);

julia> is_on_curve(E, [1, -2])
true

julia> is_on_curve(E, [1, -1])
false
```
