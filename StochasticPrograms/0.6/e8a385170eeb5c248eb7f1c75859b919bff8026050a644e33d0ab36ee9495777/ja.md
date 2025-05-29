```
outcome_model(stochasticprogram::TwoStageStochasticProgram,
              decision::AbstractVector,
              scenario::AbstractScenario;
              optimizer = nothing)
```

提供された `scenario` において `decision` が第一段階の決定である場合、`stochasticprogram` から結果の第二段階モデルを返します。供給された `decision` は `stochasticprogram` に定義された決定変数と一致する必要があります。オプションで、結果モデルに適切な `optimizer` を供給してください。
