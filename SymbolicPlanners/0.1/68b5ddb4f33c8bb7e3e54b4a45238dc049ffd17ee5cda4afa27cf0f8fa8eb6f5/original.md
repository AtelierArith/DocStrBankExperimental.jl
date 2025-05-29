```
MinStepsGoal(terms)
MinStepsGoal(goal::Term)
MinStepsGoal(problem::Problem)
```

[`Goal`](@ref) specification where each step (i.e. action) has unit cost,  and the goal formula is a conjunction of `terms`. Planners called with this specification will try to minimize the number of steps to the goal in the returned [`Solution`](@ref).
