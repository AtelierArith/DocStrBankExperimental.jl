```
relative_gap(model::StochasticProgram, stage::Integer, scenario_index::Integer)
```

ステージ `stage` とシナリオ `scenario_index` のノードにおける最終的な相対最適性ギャップを返します。これは `optimize!(stochasticprogram)` の呼び出し後の値です。
