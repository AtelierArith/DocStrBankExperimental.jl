```
split_at(v::T, i::Int) -> Tuple{T, T} where {T <: MemoryView}
```

Split a memory view into two at an index.

The first will contain all indices in `1:i-1`, the second `i:end`. This function will throw a `BoundsError` if `i` is not in `1:end+1`.

# Examples

```jldocstest
julia> split_at(MemoryView([1,2,3,4,5]), 2)
([1], [2, 3, 4, 5])

julia> split_at(MemoryView(Int8[1, 2, 3]), 4)
(Int8[1, 2, 3], Int8[])
```
