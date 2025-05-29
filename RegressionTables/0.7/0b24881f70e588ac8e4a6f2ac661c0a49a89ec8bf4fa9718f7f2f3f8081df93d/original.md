```
struct RegressionType{T}
    val::T
    is_iv::Bool
end
```

The type of the regression. `val` should be a distribution from the [Distributions.jl](https://github.com/JuliaStats/Distributions.jl) package. `is_iv` indicates whether the regression is an instrumental variable regression. The default label for the regression type is "Estimator". The labels for individual regression types (e.g., "OLS", "Poisson") can be set by running:

```julia
RegressionTables.label_ols(render::AbstractRenderType) = $name
RegressionTables.label_iv(render::AbstractRenderType) = $name
```

Or for individual distributions by running:

```julia
Base.repr(render::AbstractRenderType, x::$Distribution; args...) = $Name
```
