```
EEV(stochasticprogram::TwoStageStochasticProgram)
```

二段階`stochasticprogram`の**期待値の期待値解**（`EEV`）を計算します。

言い換えれば、`EVP`決定を評価します。最適化器がまだ設定されていない場合（[`set_optimizer`](@ref)を参照）、`NoOptimizer`エラーがスローされます。

関連情報: [`EVP`](@ref), [`EV`](@ref)
