```
confint(pr::MixedModelProfile; level::Real=0.95)
```

Compute profile confidence intervals for coefficients and variance components, with confidence level level (by default 95%).

!!! note
    The API guarantee is for a Tables.jl compatible table. The exact return type is an implementation detail and may change in a future minor release without being considered breaking.


!!! note
    The "row names" indicating the associated parameter name are guaranteed to be unambiguous, but their precise naming scheme is not yet stable and may change in a future release without being considered breaking.

