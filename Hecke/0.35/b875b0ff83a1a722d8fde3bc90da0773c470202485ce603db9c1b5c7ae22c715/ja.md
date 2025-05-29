```
parent(P::EllipticCurvePoint) -> EllipticCurve
```

$$
P
$$

が存在する楕円曲線を返します。

# 例

```jldoctest
julia> E = elliptic_curve(QQ, [1, 2]);

julia> P = E([1, -2]);

julia> E == parent(P)
true
```
