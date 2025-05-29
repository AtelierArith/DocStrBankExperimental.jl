```
GetModel(func::ODEFunction, u0::AbstractArray, ObservationFunction::Function; tol::Real=1e-7, meth::AbstractODEAlgorithm=Tsit5(), Domain::Union{HyperCube,Nothing}=nothing, inplace::Bool=true)
```

Returns a `ModelMap` which evolves the given system of ODEs from the initial configuration `u0` and afterwards applies the `ObservationFunction` to produce its predictions.

`ObservationFunction` should either be of the form `F(u) -> Vector` or `F(u,t) -> Vector` or `F(u,t,θ) -> Vector`. Internally, the `ObservationFunction` is automatically wrapped as `F(u,t,θ)` if it is not already defined to accept three arguments.

A `Domain` can be supplied to constrain the parameters of the model to particular ranges which can be helpful in the fitting process.
