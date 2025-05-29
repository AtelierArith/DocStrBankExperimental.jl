```
dimension_indices(z::PVector{T, N})
dimension_indices(dims::NTuple{N, Int})
```

Return a tuple of `N` `UnitRange`s indexing the underlying data.

## Example

```julia-repl
julia> v = PVector([4, 5, 6], [2, 3], [1, 2])
PVector{Int64, 3}:
 [4, 5, 6] × [2, 3] × [1, 2]

julia> dimension_indices(v)
(1:3, 4:5, 6:7)
```
