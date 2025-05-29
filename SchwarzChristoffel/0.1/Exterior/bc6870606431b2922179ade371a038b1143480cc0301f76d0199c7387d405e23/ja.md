```
Jmoment(m::ConformalMap) -> Float64
```

マッピング `m` によって記述される形状の第二面積モーメントを返します。

# 例

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> Jmoment(m)
1.5768333333333333
```
