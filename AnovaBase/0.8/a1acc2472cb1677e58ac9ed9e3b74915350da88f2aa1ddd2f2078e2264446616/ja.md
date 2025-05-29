```
anova(Test::Type{<: GoodnessOfFit}, <anovamodel>; <keyword arguments>)
anova(<models>...; test::Type{<: GoodnessOfFit}, <keyword arguments>)
anova(Test::Type{<: GoodnessOfFit}, <model>; <keyword arguments>)
anova(Test::Type{<: GoodnessOfFit}, <models>...; <keyword arguments>)
```

分散分析。

`AnovaResult{M, Test, N}`を返します。詳細については[`AnovaResult`](@ref)を参照してください。

  * `anovamodel`: [`AnovaModel`](@ref)です。
  * `models`: `RegressionModel`(s)。複数のモデルが提供される場合、それらはネストされている必要があり、同じデータでフィッティングされ、最後のモデルが最も複雑である必要があります。
  * `Test`: 適合度のための検定統計量。利用可能な検定は[`LikelihoodRatioTest`](@ref)（`LRT`）と[`FTest`](@ref)です。
