```
MinMetricGoal(terms, metric::Term)
MinMetricGoal(goal::Term, metric::Term)
MinMetricGoal(problem::Problem)
```

[`Goal`](@ref) specification where each step has a cost specified by the  difference in values of a `metric` formula between the next state and the current state, and the goal formula is a conjuction of `terms`.Planners called with this specification will try to minimize the `metric` formula when solving for the goal.
