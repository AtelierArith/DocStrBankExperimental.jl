```
UnionAll
```

型パラメータのすべての値にわたる型の和。`UnionAll`は、いくつかのパラメータの値が不明な場合のパラメトリック型を説明するために使用されます。

# 例

```jldoctest
julia> typeof(Vector)
UnionAll

julia> typeof(Vector{Int})
DataType
```
