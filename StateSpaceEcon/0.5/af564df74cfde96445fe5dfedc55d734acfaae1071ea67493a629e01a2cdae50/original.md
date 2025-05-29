```
steadystatedata(model, plan; [ref=firstdate(plan) + m.maxlag))
```

Create a [`SimData`](@ref) for a simulation with the given `model` and `plan`. Columns correspond to the model variables and shocks in the correct order. Data is initialized with the steady state.

In the case of steady state solution that is not stationary (i.e., non-zero slope) use the `ref` option to specify the period in which the steady state level is given. The default for `ref` is the first simulation period.

See also [`zeroarray`](@ref) and [`zeroworkspace`](@ref)
