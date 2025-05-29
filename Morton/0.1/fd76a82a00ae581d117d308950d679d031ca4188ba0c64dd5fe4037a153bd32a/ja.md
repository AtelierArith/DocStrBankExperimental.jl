```
cartesian3morton(c::AbstractVector) -> m::Integer
```

3次元デカルト座標を与えると、対応するモートン番号を返します。

# 例

```jldoctest
julia> cartesian3morton([5,2,1])
67
```
