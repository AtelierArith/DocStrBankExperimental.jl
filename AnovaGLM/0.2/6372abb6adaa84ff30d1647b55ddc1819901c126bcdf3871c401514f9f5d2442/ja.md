```
anova(<glmmodels>...; test::Type{<: GoodnessOfFit},  <keyword arguments>)
anova(<anovamodel>; test::Type{<: GoodnessOfFit},  <keyword arguments>)
anova(test::Type{<: GoodnessOfFit}, <glmmodels>...;  <keyword arguments>)
anova(test::Type{<: GoodnessOfFit}, <anovamodel>;  <keyword arguments>)
```

分散分析。

`AnovaResult{M, test, N}`を返します。詳細については[`AnovaResult`](@ref)を参照してください。

# 引数

  * `glmmodels`: モデルオブジェクト

    1. `TableRegressionModel{<: LinearModel}`は`GLM.lm`によってフィッティングされます。
    2. `TableRegressionModel{<: GeneralizedLinearModel}`は`GLM.glm`によってフィッティングされます。

    複数のモデルが提供される場合、それらはネストされている必要があり、最後のモデルが最も複雑です。
  * `anovamodel`: ラップされたモデルオブジェクト; `FullModel`および`NestedModels`。
  * `test`: 適合度のための検定統計量。利用可能なテストは[`LikelihoodRatioTest`](@ref) ([`LRT`](@ref))および[`FTest`](@ref)です。デフォルトはモデルタイプに基づいています。

    1. `TableRegressionModel{<: LinearModel}`: `FTest`。
    2. `TableRegressionModel{<: GeneralizedLinearModel}`: 分布関数に基づいています。`canonicalgoodnessoffit`を参照してください。

# その他のキーワード引数

  * モデルが1つ提供される場合:  

    1. `type`はanovaのタイプ（1、2、または3）を指定します。デフォルト値は1です。
  * 複数のモデルが提供される場合:  

    1. `check`: モデルがネストされているかどうかを確認できます。デフォルト値はtrueです。一部のチェック機能は現在実装されていません。

!!! note
    新しいモデルをフィッティングし、同時にanovaを実施するには、`LinearModel`のための[`anova_lm`](@ref)および`GeneralizedLinearModel`のための[`anova_glm`](@ref)を参照してください。

