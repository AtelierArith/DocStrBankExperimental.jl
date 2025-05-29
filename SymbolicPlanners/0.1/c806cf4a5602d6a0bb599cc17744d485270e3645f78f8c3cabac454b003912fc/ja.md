```
MaxMetricGoal(goals, metric::Term)
MaxMetricGoal(goal::Term, metric::Term)
MaxMetricGoal(problem::Problem)
```

[`Goal`](@ref) 仕様では、各ステップに報酬が指定されており、次の状態と現在の状態の間の `metric` 公式の値の差によって決まります。また、目標公式は `terms` の結合です。この仕様で呼び出されたプランナーは、目標を解決する際に `metric` 公式を最大化しようとします。
