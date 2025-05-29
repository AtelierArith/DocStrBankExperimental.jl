```
evaluate_decision(stochasticprogram::TwoStageStochasticProgram, decision::AbstractVector)
```

`stochasticprogram`における第一段階の`decision`を評価します。

言い換えれば、`decision`における第一段階の目的を評価し、すべての利用可能なシナリオに対して`decision`の結果モデルを解決します。提供された`decision`は、`stochasticprogram`で定義された意思決定変数と一致する必要があります。もし`stochasticprogram`の最適解が決定されているが、[`cache_solution!`](@ref)が呼び出されていない場合、この呼び出しによって解が上書きされます。もしまだオプティマイザーが設定されていない場合（[`set_optimizer`](@ref)を参照）、`NoOptimizer`エラーがスローされます。
