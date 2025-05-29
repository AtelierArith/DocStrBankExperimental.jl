```
EWS(stochasticprogram::StochasticProgram)
```

`stochasticprogram`の**期待待機結果**（`EWS`）を計算します。

言い換えれば、`stochasticprogram`に提供されたシナリオを使用して、すべての可能な待機モデルの期待結果を計算します。

まだオプティマイザーが設定されていない場合（[`set_optimizer`](@ref)を参照）、`NoOptimizer`エラーがスローされます。

関連情報: [`VRP`](@ref), [`WS`](@ref)
