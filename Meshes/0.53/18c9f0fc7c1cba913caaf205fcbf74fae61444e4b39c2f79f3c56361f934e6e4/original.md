```
RegularRefinement(f₁, f₂, ..., fₙ)
```

Refine each dimension of the grid by given factors `f₁`, `f₂`, ..., `fₙ`.

## Examples

```julia
refine(grid2D, RegularRefinement(2, 3))
refine(grid3D, RegularRefinement(2, 3, 1))
```
