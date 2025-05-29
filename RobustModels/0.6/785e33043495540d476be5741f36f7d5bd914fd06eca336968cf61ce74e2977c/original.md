```
refit!(m::RobustLinearModel, [y::FPVector];
                             wts::Union{Nothing, FPVector} = nothing,
                             offset::Union{Nothing, FPVector} = nothing,
                             quantile::Union{Nothing, AbstractFloat} = nothing,
                             ridgeλ::Union{Nothing, Real} = nothing,
                             kwargs...)
```

Refit the [`RobustLinearModel`](@ref).

This function assumes that `m` was correctly initialized and the model is refitted with the new values for the response, weights, offset, quantile and ridge shrinkage.

Defining a new `quantile` is only possible for [`GeneralizedQuantileEstimator`](@ref).

Defining a new `ridgeλ` is only possible for [`RidgePred`](@ref) objects.
