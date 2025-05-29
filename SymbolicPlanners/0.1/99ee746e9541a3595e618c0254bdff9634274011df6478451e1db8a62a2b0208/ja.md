```
MinMetricGoal(terms, metric::Term)
MinMetricGoal(goal::Term, metric::Term)
MinMetricGoal(problem::Problem)
```

[`Goal`](@ref) の仕様では、各ステップのコストは次の状態と現在の状態の間の `metric` 公式の値の差によって指定され、目標公式は `terms` の結合です。この仕様で呼び出されたプランナーは、目標を解決する際に `metric` 公式を最小化しようとします。
