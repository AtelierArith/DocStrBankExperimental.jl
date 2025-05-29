```
steadystateworkspace(model, plan; [ref=firstdate(plan) + m.maxlag))
```

Create a [`Workspace`](@ref TimeSeriesEcon.Workspace) containing a [`TSeries`](@ref TimeSeriesEcon.TSeries) for each variable/shock in the given `model`. They are initialized to the steady state solution.

In the case of steady state solution that is not stationary (i.e., non-zero slope) use the `ref` option to specify the period in which the steady state level is given. The default for `ref` is the first simulation period.

We recommend using [`steadystatedata`](@ref). See also [`steadystatearray`](@ref).
