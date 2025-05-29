```
anova(<glmmodels>...; test::Type{<: GoodnessOfFit},  <keyword arguments>)
anova(<anovamodel>; test::Type{<: GoodnessOfFit},  <keyword arguments>)
anova(test::Type{<: GoodnessOfFit}, <glmmodels>...;  <keyword arguments>)
anova(test::Type{<: GoodnessOfFit}, <anovamodel>;  <keyword arguments>)
```

Analysis of variance.

Return `AnovaResult{M, test, N}`. See [`AnovaResult`](@ref) for details.

# Arguments

  * `glmmodels`: model objects

    1. `TableRegressionModel{<: LinearModel}` fitted by `GLM.lm`
    2. `TableRegressionModel{<: GeneralizedLinearModel}` fitted by `GLM.glm`

    If mutiple models are provided, they should be nested and the last one is the most complex.
  * `anovamodel`: wrapped model objects; `FullModel` and `NestedModels`.
  * `test`: test statistics for goodness of fit. Available tests are [`LikelihoodRatioTest`](@ref) ([`LRT`](@ref)) and [`FTest`](@ref). The default is based on the model type.

    1. `TableRegressionModel{<: LinearModel}`: `FTest`.
    2. `TableRegressionModel{<: GeneralizedLinearModel}`: based on distribution function, see `canonicalgoodnessoffit`.

# Other keyword arguments

  * When one model is provided:  

    1. `type` specifies type of anova (1, 2 or 3). Default value is 1.
  * When multiple models are provided:  

    1. `check`: allows to check if models are nested. Defalut value is true. Some checkers are not implemented now.

!!! note
    For fitting new models and conducting anova at the same time, see [`anova_lm`](@ref) for `LinearModel`, [`anova_glm`](@ref) for `GeneralizedLinearModel`.

