```
StateConstrainedGoal(goal::Goal, constraints::Vector{Term})
```

[`Goal`](@ref) specification with a list of `constraints` that must hold for every state. Planners that receive this specification are required to return plans or policies that ensure every visited state satisfies the constraints.
