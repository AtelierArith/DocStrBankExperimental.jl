```
isinpoly(z::Complex128,p::Polygon) -> Bool
```

`z`が多角形`p`の内側にあるか外側にあるかに応じて、`true`または`false`を返します。

# 例

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> isinpoly(0.0+0.0im,p)
true

julia> isinpoly(1.0+2.0im,p)
false
```
