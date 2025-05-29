```
StatsAPI.fit(::Type{<:PowerTransformation}, y::AbstractVector{<:Number}; atol=1e-8,
             algorithm::Symbol=:LN_BOBYQA, opt_atol=1e-8, opt_rtol=1e-8,
            maxiter=-1)
StatsAPI.fit(::Type{<:PowerTransformation}, X::AbstractMatrix{<:Number},
             y::AbstractVector{<:Number}; atol=1e-8,
             algorithm::Symbol=:LN_BOBYQA, opt_atol=1e-8, opt_rtol=1e-8,
             maxiter=-1)
StatsAPI.fit(::Type{<:PowerTransformation}, formula::FormulaTerm, data;
             atol=1e-8,
             algorithm::Symbol=:LN_BOBYQA, opt_atol=1e-8, opt_rtol=1e-8,
             maxiter=-1)
StatsAPI.fit(::Type{<:PowerTransformation}, model::LinearMixedModel;
             atol=1e-8, progress=true,
             algorithm::Symbol=:LN_BOBYQA, opt_atol=1e-8, opt_rtol=1e-8,
             maxiter=-1)
```

Find the optimal λ value for a power transformation of the data.

When no `X` is provided, `y` is treated as an unconditional distribution.

When `X` is provided, `y` is treated as distribution conditional on the linear predictor defined by `X`. At each iteration step, a simple linear regression is fit to the transformed `y` with `X` as the model matrix.

If a `FormulaTerm` is provided, then `X` is constructed using that specification and `data`.

If a `LinearMixedModel` is provided, then `X` and `y` are extracted from the model object.

!!! note
    The formula interface is only available if StatsModels.jl is loaded either directly or via another package such GLM.jl or MixedModels.jl.


!!! note
      * The formula interface is defined as a package extension.
      * The MixedModels interface is defined as a package extension.


`atol` controls the absolute tolerance for treating `λ` as zero.

The `opt_` keyword arguments are tolerances passed onto NLopt.

`maxiter` specifies the maximum number of iterations to use in optimization; negative values place no restrictions.

`algorithm` is a valid NLopt algorithm to use in optimization.

`progress` enables progress bars for intermediate model fits during the optimization process.
