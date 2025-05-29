```
mergedims(dims, old_dims => new_dim, others::Pair...) => dims_new
```

If dimensions `old_dims`, `new_dim`, etc. are found in `dims`, then return new `dims_new` where all dims in `old_dims` have been combined into a single dim `new_dim`. The returned dimension will keep only the name of `new_dim`. Its coords will be a [`MergedLookup`](@ref) of the coords of the dims in `old_dims`. New dimensions are always placed at the end of `dims_new`. `others` contains other dimension pairs to be merged.

# Example

```jldoctest
julia> using DimensionalData

julia> ds = (X(0:0.1:0.4), Y(10:10:100), Ti([0, 3, 4]))
(↓ X  0.0:0.1:0.4,
→ Y  10:10:100,
↗ Ti [0, 3, 4])

julia> mergedims(ds, (X, Y) => :space)
(↓ Ti    [0, 3, 4],
→ space MergedLookup{Tuple{Float64, Int64}} [(0.0, 10), (0.1, 10), …, (0.3, 100), (0.4, 100)] (↓ X, → Y))
```
