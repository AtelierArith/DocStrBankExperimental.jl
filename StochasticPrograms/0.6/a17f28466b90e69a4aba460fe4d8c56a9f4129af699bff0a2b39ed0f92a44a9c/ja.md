```
add_scenario!(scenariogenerator::Function, stochasticprogram::StochasticProgram, stage::Integer)
```

`scenariogenerator`によって返されたシナリオを`stochasticprogram`の`stage`に格納します。`stochasticprogram`が分散している場合、シナリオは現在最も少ないシナリオを持つノードで定義されます。
