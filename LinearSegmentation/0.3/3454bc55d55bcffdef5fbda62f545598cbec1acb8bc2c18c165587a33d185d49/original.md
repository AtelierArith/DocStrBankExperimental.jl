```julia
shortest_path(
    xs,
    ys;
    min_segment_length,
    fit_threshold,
    fit_function,
    overlap
) -> Vector{Vector{Int64}}

```

Partition `xs` into segments that are at least longer than `min_segment_length`, and that have a fit better than `fit_threshold`. By default, the goodness-of-fit is measured using the coefficient of determination. Each segment must have a minimum R² of `fit_threshold`. Root mean squared error can also be used by setting `fit_function = :rmse`, and adjusting `fit_threshold` to a dataset dependent error threshold. In this case, the root mean squared error must be smaller than `fit_threshold`.

Builds a directed graph where nodes are the x-data points, and the edge weights are the goodness-of-fit measure associated with a linear model between these nodes. Nodes are connected only if their minimum length is greater than `min_segment_length`, and the goodness-of-fit better than `fit_threshold`. By default, the end of a segment is also the start of the next segment, but this can be changed by setting `overlap` to `false` (resulting in disjoint segmentations). Thereafter, the shortest weighted path spanning the entire dataset is found using the A-star algorithm. This more-or-less corresponds to the dynamic programming approach used by other segmentation algorithms. 

Sorts data internally as a precomputation step. This is the slowest algorithm, but should return a segmentation where the segments are as long as possible, balanced against their fit.

Returns an array of indices `[idxs1, ...]`, where `idxs1` are the indices of `xs` in the first segment, etc.

# Example

```
segments = shortest_path(xs, ys; min_segment_length=1.2)
```

See also: [`sliding_window`](@ref), [`top_down`](@ref).
