```
Upscale(f₁, f₂, ..., fₙ)
```

Upscale each dimension of the grid by given factors `f₁`, `f₂`, ..., `fₙ`.

This transform is equivalent to skipping entries of the grid as in the pseudo-code `grid[1:f₁:end, 1:f₂:end, ..., 1:fₙ:end]`.

Resulting values are obtained with the [`Aggregate`](@ref) transform and its default aggregation functions.

# Examples

```julia
Upscale(2, 2)
Upscale(3, 3, 2)
```
