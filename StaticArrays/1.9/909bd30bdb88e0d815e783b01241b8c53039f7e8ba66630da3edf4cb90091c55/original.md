```
setindex(vec::StaticArray, x, index::Int)
```

Return a new array with the item at `index` replaced by `x`.

# Examples

```jldoctest
julia> setindex(@SVector[1,2,3], 4, 2)
3-element SVector{3, Int64} with indices SOneTo(3):
 1
 4
 3

julia> setindex(@SMatrix[2 4; 6 8], 1, 2)
2×2 SMatrix{2, 2, Int64, 4} with indices SOneTo(2)×SOneTo(2):
 2  4
 1  8
```
