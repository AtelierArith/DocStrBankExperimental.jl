```
add_scenario!(stochasticprogram::StochasticProgram, stage::Integer, scenario::AbstractScenario)
```

第二段階の `scenario` を `stage` の `stochasticprogram` に格納します。

`stochasticprogram` が分散している場合、シナリオは現在最も少ないシナリオを持つノードで定義されます。
