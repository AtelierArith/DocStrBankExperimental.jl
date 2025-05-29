```
range(i::Interval{:closed,:open}; length)
range(i::Interval{:closed,:open}, length::Integer)
range(i::Interval{:open,:closed}; length)
range(i::Interval{:open,:closed}, length::Integer)
```

指定された長さの範囲を `step=width(i)/length` で構築します。

# 例

```jldoctest
julia> range(iv"[1, 2)", 7)  # 右端点を含まない
1.0:0.14285714285714285:1.8571428571428572

julia> range(iv"(1, 2]", 7)  # 左端点を含まない
1.1428571428571428:0.14285714285714285:2.0

julia> range(1, 2, 8)
1.0:0.14285714285714285:2.0
```
