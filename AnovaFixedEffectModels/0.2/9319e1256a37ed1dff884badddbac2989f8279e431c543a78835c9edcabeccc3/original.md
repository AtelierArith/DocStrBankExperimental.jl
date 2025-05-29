```
anova(<lfemodels>...; test::Type{<: GoodnessOfFit})
anova(<anovamodel>; test::Type{<: GoodnessOfFit})
anova(test::Type{<: GoodnessOfFit}, <lfemodels>...;  <keyword arguments>)
anova(test::Type{<: GoodnessOfFit}, <anovamodel>;  <keyword arguments>)
```

Analysis of variance.

Return `AnovaResult{M, test, N}`. See [`AnovaResult`](@ref) for details.

# Arguments

  * `lfemodels`: model objects

      * `FixedEffectModel` fitted by `AnovaFixedEffectModels.lfe` or `FixedEffectModels.reg`.

    If mutiple models are provided, they should be nested and the last one is the most complex.
  * `anovamodel`: wrapped model objects; `FullModel` and `NestedModels`.
  * `test`: test statistics for goodness of fit. Only `FTest` is available now.

# Other keyword arguments

  * When one model is provided:  

    1. `type` specifies type of anova. Default value is 1.
  * When multiple models are provided:  

    1. `check`: allows to check if models are nested. Defalut value is true. Some checkers are not implemented now.

!!! note
    For fitting new models and conducting anova at the same time, see [`anova_lfe`](@ref) for `FixedEffectModel`.

