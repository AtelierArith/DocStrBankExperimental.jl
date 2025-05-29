```
add_scenarios!(scenariogenerator::Function, stochasticprogram::StochasticProgram, stage::Integer, n::Integer)
```

`scenariogenerator`を使用して`n`のシナリオを生成し、`stochasticprogram`の`stage`に保存します。`stochasticprogram`が分散している場合、シナリオはワーカー間で均等に分配されます。
