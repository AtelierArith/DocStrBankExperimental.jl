```
DimIndices(idx::Vector{Vector{Int}})
```

DimIndices represent an exhaustive list of indices for the  dimensions of an array. It is an object containing a single element, `idx`, which is a nested vector of integers;  e.g., `[[2], [1, 3], [4]]`. DimIndices objects are checked for  uniqueness and completeness, i.e., all indices up to the largest index are used exactly once.

# Fields

  * `idx::Vector{Vector{Int}}`: nested vector of dimension indices.

# Examples

```julia-repl
julia> DimIndices([2, [1, 3], 4])
Indices for 4D array:
[[2], [1, 3], [4]]
```
