```
decode(arr::AbstractArray)
```

上三角行列から辞書型に変換します。

# 例

```jldoctest
julia> a = reshape(1:9, 3, 3)

julia> a
3×3 reshape(::UnitRange{Int64}, 3, 3) with eltype Int64:
 1  4  7
 2  5  8
 3  6  9

julia> decode(a)
OrderedCollections.OrderedDict{Tuple{Int64,Int64},Int64} with 3 entries:
  (1, 2) => 4
  (1, 3) => 7
  (2, 3) => 8
```
