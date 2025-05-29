```
EVPI(stochasticprogram::TwoStageStochasticProgram)
```

二段階`stochasticprogram`の**完全情報の期待値**（`EVPI`）を計算します。

言い換えれば、`VRP`と`EWS`の間のギャップを計算します。最適化プログラムがまだ設定されていない場合（[`set_optimizer`](@ref]を参照）、`NoOptimizer`エラーがスローされます。

関連情報: [`VRP`](@ref), [`EWS`](@ref), [`VSS`](@ref)
