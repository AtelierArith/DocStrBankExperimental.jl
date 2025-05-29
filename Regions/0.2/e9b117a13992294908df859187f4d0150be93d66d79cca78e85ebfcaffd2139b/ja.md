```
invert(x::UnitRange{Int64})
```

範囲を反転します。反転は、原点で範囲を鏡映します。範囲は、その各座標を反転させて逆にすることによって反転されます。

```jldoctest
julia> using Regions

julia> invert(5:10)
-10:-5

julia> invert(invert(0:100))
0:100
```
