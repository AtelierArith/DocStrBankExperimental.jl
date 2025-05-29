```
MultiGoalReward(goals::Vector{Term}, rewards::Vector{Float64}, discount=1.0)
```

[`Goal`](@ref) specification where multiple `goals` have associated `rewards`. Achieving a goal delivers the associated reward. Each action has zero cost.
