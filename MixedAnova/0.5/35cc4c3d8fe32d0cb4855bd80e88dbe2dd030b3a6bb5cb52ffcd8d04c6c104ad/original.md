```
anova(::Type{FTest}, <model>; kwargs...)
anova(::Type{FTest}, <models>...; kwargs...)
```

Analysis of Variance by F-test.

Return `AnovaResult{M, FTest, N}`. See [`AnovaResult`](@ref) for details.

  * `type` specifies type of anova: 

    1. One `LinearModel` or `GeneralizedLinearModel`: 1, 2, 3 are valid
    2. One `LinearMixedModel`: 1, 3 are valid.
    3. Others: only 1 is valid.
  * `adjust_sigma` determines if adjusting to REML when `LinearMixedModel` is fitted by maximum likelihood.

!!! note
    The result with `adjust_sigma` will be slightly deviated from that of model fitted directly by REML.

