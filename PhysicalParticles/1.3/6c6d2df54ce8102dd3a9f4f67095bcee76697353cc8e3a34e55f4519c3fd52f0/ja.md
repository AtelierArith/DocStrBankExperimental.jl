```
function datadimension
```

データが単位あり/単位なしおよび2D/3Dであるかを指定するためのトレイト関数。

## 例

```jl
julia> datadimension(PVector2D())
Unitless2D()

julia> datadimension(PVector())
Unitless3D()

julia> datadimension(Star2D(uAstro))
Physical2D()

julia> datadimension(Star(uAstro))
Physical3D()

julia> datadimension([PVector2D()])
Unitless2D()

julia> datadimension([PVector()])
Unitless3D()

julia> datadimension([Star2D(uAstro)])
Physical2D()

julia> datadimension([Star(uAstro)])
Physical3D()
```
