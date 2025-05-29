```
translate(x::UnitRange{Int64}, y::Integer)
```

範囲を移動します。範囲は、その各座標にオフセットを加えることによって移動されます。

translate メソッドに加えて、+ または - 演算子を使用して範囲を移動することもできます。

```jldoctest
julia> using Regions

julia> translate(0:10, 5)
5:15

julia> (5:15) + 10
15:25

julia> 10 + (5:15)
15:25

julia> (5:15) - 10
-5:5
```
