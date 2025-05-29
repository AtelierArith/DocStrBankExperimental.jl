```
zeroarray(model, plan)
```

Create a `Matrix{Float64}` of the proper dimension for a simulation with the given model with the given plan. It is initialized to 0.

This function returns a `Matrix`. We recommend using [`zerodata`](@ref), which returns [`SimData`](@ref). See also [`zeroworkspace`](@ref)

!!! note "Deprecation Note"
    `zeroarray(model, range)` will be removed in future versions. Always create a simulation `Plan` explicitly.

