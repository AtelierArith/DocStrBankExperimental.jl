```
PlotScalar(F::Function, PlotPlane::Plane, PlanarCube::HyperCube; N::Int=100, Save::Bool=false, parallel::Bool=false, nlevels::Int=40, kwargs...)
```

スカラー関数 `F` をプロットします。これは、与えられた `PlotPlane` を 2D ドメイン `PlanarCube` 上で評価し、規則的なグリッド上で `N^2` 回評価することによって行われます。
