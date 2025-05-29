```
PlotScalar(F::Function, PlotPlane::Plane, PlanarCube::HyperCube; N::Int=100, Save::Bool=false, parallel::Bool=false, nlevels::Int=40, kwargs...)
```

Plots a scalar function `F` by evaluating the given `PlotPlane` over the 2D domain `PlanarCube` by `N^2` evaluations on a regular grid.
