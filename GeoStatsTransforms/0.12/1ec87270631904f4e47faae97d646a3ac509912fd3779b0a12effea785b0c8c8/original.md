```
Downscale(f₁, f₂, ..., fₙ)
```

Downscale each dimension of the grid by given factors `f₁`, `f₂`, ..., `fₙ`.

Resulting values are obtained with the [`Transfer`](@ref) transform.

# Examples

```julia
Downscale(2, 2)
Downscale(3, 3, 2)
```
