```
splitdimsview(array, [dims])
```

Lazily split the contents of `array` into a nested array of arrays. The outermost array contains the specified dimension(s) `dims`, which may be an integer, a tuple of integers, or defaults to the final array dimension. The nested arrays will contain all the remaining dimensions (in ascending order).

See also `splitdims`, which performs a similar operation eagerly.

#### Examples:

```julia
julia> splitdims([1 2; 3 4])
2-element SplitDimsArray{SubArray{Int64,1,Array{Int64,2},Tuple{Base.Slice{Base.OneTo{Int64}},Int64},true},1,(2,),Array{Int64,2}}:
 [1, 3]
 [2, 4]

julia> splitdims([1 2; 3 4], 1)
2-element SplitDimsArray{SubArray{Int64,1,Array{Int64,2},Tuple{Int64,Base.Slice{Base.OneTo{Int64}}},true},1,(1,),Array{Int64,2}}:
 [1, 2]
 [3, 4]
```
