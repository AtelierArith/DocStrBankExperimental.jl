```
dimension_indices_homvars(z::PVector{T, N})
dimension_indices_homvars(dims::NTuple{N, Int})
```

Return a tuple of `N` `(UnitRange, Int)` tuples indexing the underlying data per vector where the last coordinate in each vector is treated separetely.

## Example

```julia-repl
julia> v = PVector([4, 5, 6], [2, 3], [1, 2])
PVector{Int64, 3}:
 [4, 5, 6] × [2, 3] × [1, 2]

 julia> dimension_indices_homvars(v)
 ((1:2, 3), (4:4, 5), (6:6, 7))
```
