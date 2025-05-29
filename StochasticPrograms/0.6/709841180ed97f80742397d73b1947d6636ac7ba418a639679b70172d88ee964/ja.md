```
fix(dvar::DecisionVariable, scenario_index::Integer, val::Number)
```

`scenario_index`で`dvar`に関連付けられたシナリオ依存の決定変数を`val`に固定します。`dvar`が変数である場合、その変数は値に固定されます。`dvar`が既知のパラメータ値である場合、その値は更新されます。
