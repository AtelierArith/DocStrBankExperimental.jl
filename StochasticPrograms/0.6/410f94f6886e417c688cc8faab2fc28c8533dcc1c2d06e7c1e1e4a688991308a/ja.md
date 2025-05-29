```
set_lower_bound(dvar::DecisionVariable, scenario_index::Integer, lower::Number)
```

シナリオ依存の決定変数 `dvar` の `scenario_index` における下限を `lower` に設定します。存在しない場合は、新しい下限制約を作成します。
