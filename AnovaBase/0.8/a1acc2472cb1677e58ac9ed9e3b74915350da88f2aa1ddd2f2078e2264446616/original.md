```
anova(Test::Type{<: GoodnessOfFit}, <anovamodel>; <keyword arguments>)
anova(<models>...; test::Type{<: GoodnessOfFit}, <keyword arguments>)
anova(Test::Type{<: GoodnessOfFit}, <model>; <keyword arguments>)
anova(Test::Type{<: GoodnessOfFit}, <models>...; <keyword arguments>)
```

Analysis of variance.

Return `AnovaResult{M, Test, N}`. See [`AnovaResult`](@ref) for details.

  * `anovamodel`: a [`AnovaModel`](@ref).
  * `models`: `RegressionModel`(s). If mutiple models are provided, they should be nested, fitted with the same data and the last one is the most complex.
  * `Test`: test statistics for goodness of fit. Available tests are [`LikelihoodRatioTest`](@ref) (`LRT`) and [`FTest`](@ref).
