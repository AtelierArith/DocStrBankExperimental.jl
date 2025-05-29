```
MaxMetricGoal(goals, metric::Term)
MaxMetricGoal(goal::Term, metric::Term)
MaxMetricGoal(problem::Problem)
```

[`Goal`](@ref) specification where each step has a reward specified by the  difference in values of a `metric` formula between the next state and the current state, and the goal formula is a conjuction of `terms`.Planners called with this specification will try to maximize the `metric` formula when solving for the goal.
