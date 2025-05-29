```
confint(pr::MixedModelBootstrap; level::Real=0.95, method=:shortest)
```

Compute bootstrap confidence intervals for coefficients and variance components, with confidence level level (by default 95%).

The keyword argument `method` determines whether the `:shortest`, i.e. highest density, interval is used or the `:equaltail`, i.e. quantile-based, interval is used. For historical reasons, the default is `:shortest`, but `:equaltail` gives the interval that is most comparable to the profile and Wald confidence intervals.

!!! note
    The API guarantee is for a Tables.jl compatible table. The exact return type is an implementation detail and may change in a future minor release without being considered breaking.


!!! note
    The "row names" indicating the associated parameter name are guaranteed to be unambiguous, but their precise naming scheme is not yet stable and may change in a future release without being considered breaking.


See also [`shortestcovint`](@ref).
