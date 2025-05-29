```
VSS(stochasticprogram::TwoStageStochasticProgram)
```

二段階`stochasticprogram`の**確率的解の価値**（`VSS`）を計算します。

言い換えれば、`EEV`と`VRP`の間のギャップを計算します。まだオプティマイザが設定されていない場合（[`set_optimizer`](@ref)を参照）、`NoOptimizer`エラーがスローされます。
