```
combinedims(array_of_arrays)
```

Combine the dimensions of a nested array structure into a new, flat array.

This is the inverse operation of `splitdims` / `splitdimsview`.

See also `combinedimsview`, the lazy version of this function.

# Example

```julia
julia> combinedims([[1, 2], [3, 4]])
2×2 Array{Int64,2}:
 1  3
 2  4
```
