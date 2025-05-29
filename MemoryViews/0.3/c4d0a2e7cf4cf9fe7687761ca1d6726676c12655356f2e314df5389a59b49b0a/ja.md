```
split_at(v::T, i::Int) -> Tuple{T, T} where {T <: MemoryView}
```

メモリビューをインデックスで2つに分割します。

最初の部分には `1:i-1` のすべてのインデックスが含まれ、2番目の部分には `i:end` が含まれます。この関数は、`i` が `1:end+1` にない場合に `BoundsError` をスローします。

# 例

```jldocstest
julia> split_at(MemoryView([1,2,3,4,5]), 2)
([1], [2, 3, 4, 5])

julia> split_at(MemoryView(Int8[1, 2, 3]), 4)
(Int8[1, 2, 3], Int8[])
```
