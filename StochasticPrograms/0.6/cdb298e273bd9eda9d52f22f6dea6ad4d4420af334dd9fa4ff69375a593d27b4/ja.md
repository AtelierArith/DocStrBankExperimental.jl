```
add_scenarios!(stochasticprogram::TwoStageStochasticProgram, scenarios::Vector{<:AbstractScenario})
```

二段階の `stochasticprogram` に `scenarios` のコレクションを格納します。`stochasticprogram` が分散されている場合、シナリオはワーカー間で均等に分配されます。
