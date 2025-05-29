```
+(P::EllipticCurvePoint, Q::EllipticCurvePoint) -> EllipticCurvePoint
```

楕円曲線上の2つの点を加算します。

# 例

```jldoctest
julia> E = elliptic_curve(QQ, [1, 2]);

julia> P = E([1, -2]);

julia> P + P
(-1 : 0 : 1)
```
