```
range(i::OpenInterval; length)
range(i::OpenInterval, length::Integer)
```

指定された長さの範囲を構築し、`step = width(i) / (length + 1)` となります。

# 例

```jldoctest
julia> range(iv"(1, 4)", 5)  # エンドポイントを含まない
1.5:0.5:3.5

julia> range(1, 4, 7)
1.0:0.5:4.0
```
