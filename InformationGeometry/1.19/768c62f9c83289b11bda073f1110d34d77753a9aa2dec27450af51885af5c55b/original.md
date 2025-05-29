```
GetModel(func::ODEFunction, SplitterFunction::Function, observables::Union{AbstractVector{<:Int},BoolArray}; tol::Real=1e-7, meth::AbstractODEAlgorithm=Tsit5(), Domain::Union{HyperCube,Nothing}=nothing, inplace::Bool=true)
```

Returns a `ModelMap` which evolves the given system of ODEs and returns `u[observables]` to produce its predictions. Here, the initial conditions for the ODEs are produced from the parameters `θ` using the `SplitterFunction` which for instance allows one to estimate them from data.

`SplitterFunction` should be of the form `F(θ) -> (u0, p)`, i.e. the output is a `Tuple` whose first entry is the initial condition for the ODE model and the second entry constitutes the parameters which go on to enter the `ODEFunction`. Typically, a fair bit of performance can be gained from ensuring that `SplitterFunction` outputs the initial condition `u0` as type `MVector` or `MArray`, if it has less than ~100 components.

A `Domain` can be supplied to constrain the parameters of the model to particular ranges which can be helpful in the fitting process.
