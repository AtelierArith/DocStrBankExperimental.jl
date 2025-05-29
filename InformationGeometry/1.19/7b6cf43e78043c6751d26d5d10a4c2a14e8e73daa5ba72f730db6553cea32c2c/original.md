```
PlotLogLikelihood(DM::AbstractDataModel, PlanarCube::HyperCube; N::Int=100, Save::Bool=true, parallel::Bool=false, nlevels::Int=40, kwargs...)
PlotLogLikelihood(DM::AbstractDataModel, PlotPlane::Plane, PlanarCube::HyperCube; N::Int=100, Save::Bool=true, parallel::Bool=false, nlevels::Int=40, kwargs...)
```

Evaluates the loglikelihood on a 2D domain via the `PlotScalar()` function.
