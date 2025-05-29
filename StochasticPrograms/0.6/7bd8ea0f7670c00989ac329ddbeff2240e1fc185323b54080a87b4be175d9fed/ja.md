```
recourse_decision(stochasticprogram::TwoStageStochasticProgram, decision::AbstractVector, scenario::AbstractScenario)
```

最初の段階の `decision` を取った後、最適なリコース決定を決定します。`scenario` は `stochasticprogram` における実際の結果です。提供された `decision` は `stochasticprogram` に定義された決定変数と一致する必要があります。まだオプティマイザが設定されていない場合（[`set_optimizer`](@ref) を参照）、`NoOptimizer` エラーがスローされます。
