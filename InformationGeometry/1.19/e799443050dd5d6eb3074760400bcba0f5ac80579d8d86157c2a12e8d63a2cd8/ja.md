```
PlotScalar(F::Function, PlanarCube::HyperCube; N::Int=100, Save::Bool=false, parallel::Bool=false, nlevels::Int=40, kwargs...)
```

スカラー関数 `F` を 2D ドメイン `PlanarCube` 上にプロットし、正方格子上で `N^2` 回評価します。
