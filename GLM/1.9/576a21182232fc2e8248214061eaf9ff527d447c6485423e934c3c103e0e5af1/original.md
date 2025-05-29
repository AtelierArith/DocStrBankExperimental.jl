```
negbin(formula, data, [link::Link];
       <keyword arguments>)
negbin(X::AbstractMatrix, y::AbstractVector, [link::Link];
       <keyword arguments>)
```

Fit a negative binomial generalized linear model to data, while simultaneously estimating the shape parameter θ. Extra arguments and keyword arguments will be passed to [`glm`](@ref).

In the first method, `formula` must be a [StatsModels.jl `Formula` object](https://juliastats.org/StatsModels.jl/stable/formula/) and `data` a table (in the [Tables.jl](https://tables.juliadata.org/stable/) definition, e.g. a data frame). In the second method, `X` must be a matrix holding values of the independent variable(s) in columns (including if appropriate the intercept), and `y` must be a vector holding values of the dependent variable. In both cases, `link` may specify the link function (if omitted, it is taken to be `NegativeBinomial(θ)`).

# Keyword Arguments

  * `initialθ::Real=Inf`: Starting value for shape parameter θ. If it is `Inf` then the initial value will be estimated by fitting a Poisson distribution.
  * `maxiter::Integer=30`: See `maxiter` for [`glm`](@ref)
  * `atol::Real=1.0e-6`: See `atol` for [`glm`](@ref)
  * `rtol::Real=1.0e-6`: See `rtol` for [`glm`](@ref)
  * `verbose::Bool=false`: See `verbose` for [`glm`](@ref)
