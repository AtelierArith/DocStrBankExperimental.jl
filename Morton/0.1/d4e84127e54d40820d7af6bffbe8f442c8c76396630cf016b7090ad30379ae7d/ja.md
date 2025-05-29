```
cartesian2morton(c::Vector) -> m::Integer
```

2次元デカルト座標を与えると、対応するモートン番号を返します。

# 例

```jldoctest
julia> cartesian2morton([5,2])
19
```
