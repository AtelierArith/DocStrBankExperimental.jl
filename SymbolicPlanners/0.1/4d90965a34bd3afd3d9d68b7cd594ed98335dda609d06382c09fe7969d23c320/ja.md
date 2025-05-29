```
StateConstrainedGoal(goal::Goal, constraints::Vector{Term})
```

[`Goal`](@ref) の仕様で、すべての状態に対して満たされなければならない `constraints` のリストを含みます。この仕様を受け取ったプランナーは、訪れたすべての状態が制約を満たすことを保証するプランまたはポリシーを返す必要があります。
