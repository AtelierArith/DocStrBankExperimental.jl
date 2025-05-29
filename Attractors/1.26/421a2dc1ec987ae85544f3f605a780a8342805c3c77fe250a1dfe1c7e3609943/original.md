```
SubdivisionBasedGrid(grid::NTuple{D, <:AbstractRange}, lvl_array::Array{Int, D})
```

Given a coarse `grid` tesselating the state space, construct a `SubdivisionBasedGrid` based on the given level array `lvl_array` that should have the same dimension as `grid`. The level array has non-negative integer values, with 0 meaning that the corresponding cell of the coarse `grid` should not be subdivided any further. Value `n > 0` means that the corresponding cell will be subdivided in total `2^n` times (along each dimension), resulting in finer cells within the original coarse cell.
