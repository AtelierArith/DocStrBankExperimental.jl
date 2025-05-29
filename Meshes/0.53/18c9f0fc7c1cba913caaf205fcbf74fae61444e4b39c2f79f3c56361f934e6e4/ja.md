```
RegularRefinement(f₁, f₂, ..., fₙ)
```

与えられた因子 `f₁`, `f₂`, ..., `fₙ` によってグリッドの各次元を細分化します。

## 例

```julia
refine(grid2D, RegularRefinement(2, 3))
refine(grid3D, RegularRefinement(2, 3, 1))
```
