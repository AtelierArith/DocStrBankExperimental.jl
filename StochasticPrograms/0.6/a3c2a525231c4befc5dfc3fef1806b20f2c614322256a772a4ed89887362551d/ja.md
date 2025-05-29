```
evaluate_decision(stochasticprogram::TwoStageStochasticProgram, decision::AbstractVector, scenario::AbstractScenario)
```

`scenario` が `stochasticprogram` の実際の結果である場合に、第一段階の `decision` を取る結果を評価します。提供された `decision` は `stochasticprogram` で定義された意思決定変数と一致する必要があります。まだオプティマイザが設定されていない場合（[`set_optimizer`](@ref) を参照）、`NoOptimizer` エラーがスローされます。
