```
range(i::ClosedInterval; step, length)
range(i::ClosedInterval, length::Integer)
```

指定されたステップまたは長さの範囲を構築します。

# 例

```jldoctest
julia> range(1..2, 8)
1.0:0.14285714285714285:2.0

julia> range(1, 2, 8)
1.0:0.14285714285714285:2.0

julia> range(1..2, step=0.2)
1.0:0.2:2.0

julia> range(1, 2, step=0.2)
1.0:0.2:2.0
```
