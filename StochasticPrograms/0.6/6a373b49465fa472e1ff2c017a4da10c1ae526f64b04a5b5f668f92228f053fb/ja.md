```
add_scenario!(scenariogenerator::Function, stochasticprogram::StochasticProgram)
```

`scenariogenerator`によって返されたシナリオを二段階の`stochasticprogram`に格納します。`stochasticprogram`が分散している場合、シナリオは現在最も少ないシナリオを持つノードで定義されます。
