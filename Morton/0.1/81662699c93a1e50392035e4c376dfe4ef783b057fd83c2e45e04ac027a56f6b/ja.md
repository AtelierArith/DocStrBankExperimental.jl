```
morton2cartesian(m::Integer) -> [x,y]
```

モートン番号を与えると、対応する2次元デカルト座標を返します。

# 例

```jldoctest
julia> morton2cartesian(19)
2-element Array{Int64,1}:
 5
 2
```
