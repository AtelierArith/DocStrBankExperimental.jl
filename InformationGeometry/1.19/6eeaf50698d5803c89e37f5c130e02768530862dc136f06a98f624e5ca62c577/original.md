```
ParameterSavingCallback(start::AbstractVector) -> (Vector{typeof(start)}, Function)
```

Produces tuple where first entry constitutes empty `Vector{typeof(start)}` array into which the parameter trajectory will be saved. Second entry is the callback function itself, which is to be added to the optimization method via the `callback` keyword argument.

# Examples

```julia
Pars, Func = ParameterSavingCallback(MLE(DM))
InformationGeometry.minimize(DM, rand(3); meth=Optim.NewtonTrustRegion(), OptimJL=false, callback=Func)
TracePlot(Pars)
```

!!! note
    Does not work for optimizers from Optim.jl unless wrapped with OptimizationOptimJL.jl, i.e. when setting keyword `OptimJL=false`.

