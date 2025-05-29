```
RegularCoarsening(f₁, f₂, ..., fₙ)
```

Coarsen each dimension of the grid by given factors `f₁`, `f₂`, ..., `fₙ`.

## Examples

```julia
coarsen(grid2D, RegularCoarsening(2, 3))
coarsen(grid3D, RegularCoarsening(2, 3, 1))
```
