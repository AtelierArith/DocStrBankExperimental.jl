```
set_upper_bound(dvar::DecisionVariable, scenario_index::Integer, upper::Number)
```

シナリオ依存の決定変数 `dvar` の `scenario_index` における上限を `upper` に設定します。存在しない場合は、新しい上限制約を作成します。
