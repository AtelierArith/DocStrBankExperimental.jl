```
steadystatearray(model, plan; [ref=firstdate(plan) + m.maxlag])
```

Create a `Matrix{Float64}` of the proper dimension for a simulation with the given model with the given plan. It is initialized to the steady state.

In the case of steady state solution that is not stationary (i.e., non-zero slope) use the `ref` option to specify the period in which the steady state level is given. The default for `ref` is the first simulation period.

This function returns a `Matrix`. We recommend using [`zerodata`](@ref), which returns [`SimData`](@ref). See also [`zeroworkspace`](@ref)

!!! note "Deprecation Note"
    `zeroarray(model, range)` will be removed in future versions. Always create a simulation `Plan` explicitly.

