```
RegularCoarsening(f₁, f₂, ..., fₙ)
```

与えられた因子 `f₁`, `f₂`, ..., `fₙ` によってグリッドの各次元を粗くします。

## 例

```julia
coarsen(grid2D, RegularCoarsening(2, 3))
coarsen(grid3D, RegularCoarsening(2, 3, 1))
```
