```
numtype(T)
```

区間の境界型を返します。

# 例

```jldoctest
julia> numtype(interval(1, 2))
Float64

julia> numtype(interval(Float32, 1, 2))
Float32
```
