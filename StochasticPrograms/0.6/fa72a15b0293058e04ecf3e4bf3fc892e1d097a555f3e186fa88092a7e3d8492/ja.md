```
set_objective_coefficient(stochasticprogram::StochasticProgram, dvar::DecisionVariable, stage::Integer, scenario_index::Integer, coefficient::Real)
```

`dvar`に関連付けられた`scenario_index`のシナリオ依存の線形目的係数を、ステージ`stage`で`coefficient`に設定します。
