```
objective_function(stochasticprogram::StochasticProgram,
                   stage::Integer,
                   scenario_index::Integer,
                   T::Type{<:AbstractJuMPScalar}=objective_function_type(model))
```

ステージ `stage` とシナリオ `scenario_index` のノードにおける目的関数を表す型 `T` のオブジェクトを返します。目的が型 `T` に変換できない場合はエラーになります。
