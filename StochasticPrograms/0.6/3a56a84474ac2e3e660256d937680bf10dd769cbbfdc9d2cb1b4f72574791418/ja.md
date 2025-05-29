```
add_scenarios!(scenariogenerator::Function, stochasticprogram::TwoStageStochasticProgram, n::Integer)
```

`scenariogenerator`を使用して`n`のシナリオを生成し、二段階の`stochasticprogram`に格納します。`stochasticprogram`が分散されている場合、シナリオはワーカー間で均等に分配されます。
