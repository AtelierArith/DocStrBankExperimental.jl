```
objective_bound(stochasticprogram::StochasticProgram, stage::Integer, scenario_index::Integer)
```

最適化関数 `optimize!(stochasticprogram)` を呼び出した後、ステージ `stage` とシナリオ `scenario_index` のノードにおける最適目的値の最良既知境界を返します。
