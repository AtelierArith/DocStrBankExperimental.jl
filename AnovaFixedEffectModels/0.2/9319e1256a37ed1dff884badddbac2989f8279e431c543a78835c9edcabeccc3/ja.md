```
anova(<lfemodels>...; test::Type{<: GoodnessOfFit})
anova(<anovamodel>; test::Type{<: GoodnessOfFit})
anova(test::Type{<: GoodnessOfFit}, <lfemodels>...;  <keyword arguments>)
anova(test::Type{<: GoodnessOfFit}, <anovamodel>;  <keyword arguments>)
```

分散分析。

`AnovaResult{M, test, N}`を返します。詳細については[`AnovaResult`](@ref)を参照してください。

# 引数

  * `lfemodels`: モデルオブジェクト

      * `FixedEffectModel`は`AnovaFixedEffectModels.lfe`または`FixedEffectModels.reg`によってフィットされます。

    複数のモデルが提供される場合、それらはネストされている必要があり、最後のモデルが最も複雑です。
  * `anovamodel`: ラップされたモデルオブジェクト；`FullModel`および`NestedModels`。
  * `test`: 適合度のためのテスト統計量。現在利用可能なのは`FTest`のみです。

# その他のキーワード引数

  * 1つのモデルが提供される場合：  

    1. `type`は分散分析のタイプを指定します。デフォルト値は1です。
  * 複数のモデルが提供される場合：  

    1. `check`: モデルがネストされているかどうかを確認できます。デフォルト値はtrueです。一部のチェック機能は現在実装されていません。

!!! note
    新しいモデルをフィットさせ、同時に分散分析を行うには、`FixedEffectModel`の[`anova_lfe`](@ref)を参照してください。

