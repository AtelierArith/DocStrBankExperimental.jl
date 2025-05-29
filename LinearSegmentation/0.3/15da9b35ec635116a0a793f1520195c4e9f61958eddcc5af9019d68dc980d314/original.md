```julia
sliding_window(
    xs,
    ys;
    min_segment_length,
    fit_threshold,
    fit_function,
    overlap
) -> Vector{Vector{Int64}}

```

Partition `xs` into segments that are at least longer than `min_segment_length`, and that have a fit better than `fit_threshold`. By default, the goodness-of-fit is measured using the coefficient of determination. Each segment must have a minimum R² of `fit_threshold`. Root mean squared error can also be used by setting `fit_function = :rmse`, and adjusting `fit_threshold` to a dataset dependent error threshold. In this case, the root mean squared error must be smaller than `fit_threshold`.

Uses a sliding window approach to segment the data: initially an empty segment is made, and data added to it until `fit_threshold` is reached. Then a new segment is made, and the process repeats until the data is exhausted.  By default, the end of a segment is also the start of the next segment, but this can be changed by setting `overlap` to `false` (resulting in disjoint segmentations). 

Sorts data internally as a precomputation step. Fastest segmentation algorithm implemented, but also the least accurate.

Returns an array of indices `[idxs1, ...]`, where `idxs1` are the indices of `xs` in the first segment, etc.

# Example

```
segments = sliding_window(xs, ys; min_segment_length=1.2, fit_threshold=0.9)
```

See also: [`top_down`](@ref), [`shortest_path`](@ref).
