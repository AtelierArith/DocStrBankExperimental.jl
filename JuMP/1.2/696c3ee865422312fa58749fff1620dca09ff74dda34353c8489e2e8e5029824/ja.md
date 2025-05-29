```
set_objective_coefficient(model::Model, variable::VariableRef, coefficient::Real)
```

`Variable`に関連付けられた線形目的係数を`coefficient`に設定します。

注意: この関数は非線形目的が設定されている場合にエラーをスローします。
