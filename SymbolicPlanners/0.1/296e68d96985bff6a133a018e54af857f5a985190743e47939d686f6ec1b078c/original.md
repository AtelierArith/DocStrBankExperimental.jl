```
HSPHeuristic(op::Function)
```

A family of relaxed planning graph heuristics, introduced by the HSP  planner [1]. The heuristic precomputes a graph that stores the dependencies between all ground actions and plan-relevant conditions. The cost of achieving each action  (and also the goal) is then recursively estimated as the aggregated cost of achieving each (pre)condition the action or goal depends upon, where `op` is an aggregation function (e.g. `max` or `+`).

In turn, the cost of achieving each condition (a.k.a. "fact") is estimated as the minimum cost among all actions that achieve that condition. Once a condition is achieved by an action, it is considered to remain true through the rest of the process, hence the relaxed nature of the heuristic.

This implementation supports domains with negative preconditions, disjunctive preconditions (i.e., `or`, `exists`), and functional preconditions (e.g. numeric comparisons, or other Boolean-valued functions of non-Boolean fluents). Functional preconditions are handled by (optimistically) assuming they become true once a constituent fluent is modified by some action.

[1] B. Bonet and H. Geffner, "Planning as Heuristic Search," Artificial Intelligence, vol. 129, no. 1, pp. 5–33, Jun. 2001, [https://doi.org/10.1016/S0004-3702(01)00108-4](https://doi.org/10.1016/S0004-3702(01)00108-4).
