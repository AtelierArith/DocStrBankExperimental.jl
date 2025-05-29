```
isinpoly(z::Complex128,p::Polygon,tol::Float64) -> Bool
```

`z`がポリゴン`p`の内部または距離`tol`以内にある場合は`true`を返します。

# 例

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> isinpoly(-1.01+0.0im,p)
false

julia> isinpoly(-1.01+0.0im,p,1e-2)
true
```
