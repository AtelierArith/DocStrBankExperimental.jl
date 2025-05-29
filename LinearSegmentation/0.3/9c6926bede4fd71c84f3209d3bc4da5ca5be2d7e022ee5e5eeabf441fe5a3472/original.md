```julia
top_down(
    xs,
    ys;
    min_segment_length,
    fit_threshold,
    fit_function,
    overlap
) -> Vector{Vector{Int64}}

```

Partition `xs` into segments that are at least longer than `min_segment_length`, and that have a fit better than `fit_threshold`. By default, the goodness-of-fit is measured using the coefficient of determination. Each segment must have a minimum R² of `fit_threshold`. Root mean squared error can also be used by setting `fit_function = :rmse`, and adjusting `fit_threshold` to a dataset dependent error threshold. In this case, the root mean squared error must be smaller than `fit_threshold`.

Recursively splits the data into two parts with the best fit according to `fit_function`, while obeying the minimum segment length restrictions from `min_segment_length`, and goodness-off-fit restrictions from `fit_threshold`. Sorts data internally as a precomputation step.  By default, the end of a segment is also the start of the next segment, but this can be changed by setting `overlap` to `false` (resulting in disjoint segmentations).

Returns an array of indices `[idxs1, ...]`, where `idxs1` are the indices of `xs` in the first segment, etc.

# Example

```
segments = top_down(xs, ys; min_segment_length=1.2)
```

See also: [`sliding_window`](@ref), [`shortest_path`](@ref).
