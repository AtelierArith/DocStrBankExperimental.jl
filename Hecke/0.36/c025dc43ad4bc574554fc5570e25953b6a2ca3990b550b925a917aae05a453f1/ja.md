```
division_points(P::EllipticCurvePoint, m::Int) -> EllipticCurvePoint
```

基底体上で定義された点の集合 $Q$ を計算します。ここで $mQ = P$ です。該当する点が存在しない場合は空のリストを返します。

# 例

```jldoctest
julia> E = elliptic_curve(QQ, [1, 2]);

julia> division_points(infinity(E), 2)
2-element Vector{EllipticCurvePoint{QQFieldElem}}:
 (0 : 1 : 0)
 (-1 : 0 : 1)
```
