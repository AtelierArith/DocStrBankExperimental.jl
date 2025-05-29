```
wait_and_see_decision(stochasticprogram::TwoStageStochasticProgram, scenario::AbstractScenario, optimizer_constructor = nothing)
```

二段階`stochasticprogram`の**待機観察**（`WS`）モデルの最適化器を、`scenario`に対応して計算します。

まだ最適化器が設定されていない場合（[`set_optimizer`](@ref)を参照）、`NoOptimizer`エラーがスローされます。

詳細については、[`WS`](@ref)を参照してください。
