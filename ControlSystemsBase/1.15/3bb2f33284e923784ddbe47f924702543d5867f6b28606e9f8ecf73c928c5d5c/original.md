```
fig = gangoffourplot(P::LTISystem, C::LTISystem; minimal=true, plotphase=false, Ms_lines = [1.0, 1.25, 1.5], Mt_lines = [], sigma = true, kwargs...)
```

Gang-of-Four plot.

`sigma` determines whether a [`sigmaplot`](@ref) is used instead of a [`bodeplot`](@ref) for MIMO `S` and `T`. `kwargs` are sent as argument to RecipesBase.plot.
