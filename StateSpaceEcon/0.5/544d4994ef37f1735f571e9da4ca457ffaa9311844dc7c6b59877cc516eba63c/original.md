```
zeroworkspace(model, plan)
```

Create a [`Workspace`](@ref TimeSeriesEcon.Workspace) containing a [`TSeries`](@ref TimeSeriesEcon.TSeries) for each variable/shock in the given `model`. They are initialized to 0.

We recommend using [`zerodata`](@ref) for simulations. See also [`zeroarray`](@ref).
