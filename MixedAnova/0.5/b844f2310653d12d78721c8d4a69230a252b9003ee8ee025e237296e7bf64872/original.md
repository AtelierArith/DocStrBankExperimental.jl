```
anova(<models>...; test::Type{<: GoodnessOfFit})
```

Analysis of variance.

Return `AnovaResult{M, test, N}`. See [`AnovaResult`](@ref) for details.

  * `models`: model objects

    1. `TableRegressionModel{<: LinearModel}` fitted by `GLM.lm`
    2. `TableRegressionModel{<: GeneralizedLinearModel}` fitted by `GLM.glm`
    3. `LinearMixedModel` fitted by `MixedAnova.lme` or `fit(LinearMixedModel, ...)`
    4. `GeneralizedLinearMixedModel` fitted by `MixedAnova.glme` or `fit(GeneralizedLinearMixedModel, ...)`
    5. `TableRegressionModel{<: FixedEffectModel}` fitted by `MixedAnova.lfe`.

    If mutiple models are provided, they should be nested and the last one is the most saturated.
  * `test`: test statistics for goodness of fit. Available tests are [`LikelihoodRatioTest`](@ref) ([`LRT`](@ref)) and [`FTest`](@ref). The default is based on the model type.

    1. `TableRegressionModel{<: LinearModel}`: `FTest`.
    2. `TableRegressionModel{<: GeneralizedLinearModel}`: based on distribution function, see `canonicalgoodnessoffit`.
    3. `LinearMixedModel`: `FTest` for one model fit; `LRT` for nested models.
    4. `GeneralizedLinearMixedModel`: `LRT` for nested models.
    5. `TableRegressionModel{<: FixedEffectModel}`: `FTest`.

When multiple models are provided:  

  * `check`: allows to check if models are nested. Defalut value is true. Some checkers are not implemented now.
  * `isnested`: true when models are checked as nested (manually or automatically). Defalut value is false.

For fitting new models and conducting anova at the same time, see [`anova_lm`](@ref) for `LinearModel`, [`anova_glm`](@ref) for `GeneralizedLinearModel`, [`anova_lme`](@ref) for `LinearMixedModel`, and [`anova_lfe`](@ref) for `FixedEffectModel`.
