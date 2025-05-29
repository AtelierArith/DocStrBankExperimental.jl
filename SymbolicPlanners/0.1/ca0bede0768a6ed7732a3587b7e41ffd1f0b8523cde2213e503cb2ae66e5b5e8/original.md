```
ActionGoal(action::Term, [constraints, step_cost])
```

[`Goal`](@ref) specification which requires that `action` is executed as the  final step. Optionally, object `constraints` can be specified. These  are either static constraints on the action's variable parameters, or predicates  that must hold in the final state. The cost of each step in the solution is `step_cost`, which defaults to 1.0.
