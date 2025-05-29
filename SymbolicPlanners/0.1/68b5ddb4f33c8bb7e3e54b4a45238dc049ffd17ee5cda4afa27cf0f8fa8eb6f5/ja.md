```
MinStepsGoal(terms)
MinStepsGoal(goal::Term)
MinStepsGoal(problem::Problem)
```

[`Goal`](@ref) の仕様では、各ステップ（すなわちアクション）のコストが単位であり、ゴールの式は `terms` の論理積です。この仕様で呼び出されたプランナーは、返される [`Solution`](@ref) においてゴールまでのステップ数を最小化しようとします。
