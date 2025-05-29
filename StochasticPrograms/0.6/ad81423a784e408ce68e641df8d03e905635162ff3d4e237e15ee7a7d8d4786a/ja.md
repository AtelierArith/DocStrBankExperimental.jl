```
expected_value_decision(stochasticprogram::TwoStageStochasticProgram)
```

二段階の `stochasticprogram` の `EVP` の最適化子を計算します。

最適化子がまだ設定されていない場合（[`set_optimizer`](@ref) を参照）、`NoOptimizer` エラーがスローされます。

関連情報: [`EVP`](@ref), [`EV`](@ref), [`EEV`](@ref)
