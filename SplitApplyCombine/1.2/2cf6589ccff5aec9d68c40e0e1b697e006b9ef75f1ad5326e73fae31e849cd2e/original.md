```
splitdims(array, [dims])
```

Eagerly split the contents of `array` into a nested array of arrays. The outermost array contains the specified dimension(s) `dims`, which may be an integer, a tuple of integers, or defaults to the final array dimension. The nested arrays will contain all the remaining dimensions (in ascending order).

See also `splitdimsview`, which performs a similar operation lazily.

#### Examples:

```julia
julia> splitdims([1 2; 3 4])
2-element Array{Array{Int64,1},1}:
 [1, 3]
 [2, 4]

julia> splitdims([1 2; 3 4], 1)
2-element Array{Array{Int64,1},1}:
 [1, 2]
 [3, 4]
```
