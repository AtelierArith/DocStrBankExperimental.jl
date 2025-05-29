```
centroid(m::ConformalMap) -> ComplexF64
```

マッピング `m` によって記述される形状の複素重心位置を返します。

# 例

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> centroid(m)
-0.20919540229885059 - 0.04022988505747128im
```
