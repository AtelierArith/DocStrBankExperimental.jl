```
anova(<models>...; test::Type{<: GoodnessOfFit})
```

分散分析。

`AnovaResult{M, test, N}`を返します。詳細については[`AnovaResult`](@ref)を参照してください。

  * `models`: モデルオブジェクト

    1. `TableRegressionModel{<: LinearModel}`は`GLM.lm`によってフィッティングされます。
    2. `TableRegressionModel{<: GeneralizedLinearModel}`は`GLM.glm`によってフィッティングされます。
    3. `LinearMixedModel`は`MixedAnova.lme`または`fit(LinearMixedModel, ...)`によってフィッティングされます。
    4. `GeneralizedLinearMixedModel`は`MixedAnova.glme`または`fit(GeneralizedLinearMixedModel, ...)`によってフィッティングされます。
    5. `TableRegressionModel{<: FixedEffectModel}`は`MixedAnova.lfe`によってフィッティングされます。

    複数のモデルが提供される場合、それらはネストされている必要があり、最後のモデルが最も飽和しています。
  * `test`: 適合度のための検定統計量。利用可能な検定は[`LikelihoodRatioTest`](@ref)（[`LRT`](@ref））および[`FTest`](@ref)です。デフォルトはモデルタイプに基づいています。

    1. `TableRegressionModel{<: LinearModel}`: `FTest`。
    2. `TableRegressionModel{<: GeneralizedLinearModel}`: 分布関数に基づいており、`canonicalgoodnessoffit`を参照してください。
    3. `LinearMixedModel`: 一つのモデルフィットに対して`FTest`；ネストされたモデルに対して`LRT`。
    4. `GeneralizedLinearMixedModel`: ネストされたモデルに対して`LRT`。
    5. `TableRegressionModel{<: FixedEffectModel}`: `FTest`。

複数のモデルが提供される場合:  

  * `check`: モデルがネストされているかどうかを確認できます。デフォルト値はtrueです。一部のチェック機能は現在実装されていません。
  * `isnested`: モデルがネストされていると確認された場合はtrue（手動または自動）。デフォルト値はfalseです。

新しいモデルをフィッティングし、同時にanovaを実施するには、`LinearModel`のための[`anova_lm`](@ref)、`GeneralizedLinearModel`のための[`anova_glm`](@ref)、`LinearMixedModel`のための[`anova_lme`](@ref)、および`FixedEffectModel`のための[`anova_lfe`](@ref)を参照してください。
