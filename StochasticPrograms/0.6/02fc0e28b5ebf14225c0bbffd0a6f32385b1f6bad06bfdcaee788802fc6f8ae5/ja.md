```
add_scenarios!(stochasticprogram::StochasticProgram, stage::Integer, scenarios::Vector{<:AbstractScenario})
```

`stochasticprogram`において`stage`で`scenarios`のコレクションを保存します。`stochasticprogram`が分散している場合、シナリオはワーカー間で均等に分配されます。
