```
morton3cartesian(m::Integer) -> [x,y,z]
```

モートン番号を与えると、対応する3次元デカルト座標を返します。

# 例

```jldoctest
julia> morton3cartesian(67)
3-element Array{Int64,1}:
 5
 2
 1
```
