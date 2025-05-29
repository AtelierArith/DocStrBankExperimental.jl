```
MultiGoalReward(goals::Vector{Term}, rewards::Vector{Float64}, discount=1.0)
```

[`Goal`](@ref) の仕様で、複数の `goals` に関連する `rewards` があります。目標を達成すると、関連する報酬が得られます。各アクションにはコストがありません。
