```
GeneralizedLinearRegressor(dist, link; kwargs...)
```

Generalized linear regression model with distribution `dist` from Distributions.jl and `link` function.

The `kwargs` are forwarded to the `GLM.glm` function from [GLM.jl](https://github.com/JuliaStats/GLM.jl).

See also [`LinearRegressor`](@ref).
