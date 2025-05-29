```
HSPRHeuristic(op::Function)
```

A family of relaxed planning graph heuristics for backward search, introduced by the HSPr planner ("r" stands for regression) [1]. The costs of achieving  a condition are estimated in the same way as the forward variant,  [`HSPHeuristic`](@ref), but this estimation is performed only once during  heuristic precomputation. During heuristic evaluation, the cost from the current partial state to the start state is estimated as the aggregated cost of each condition that is true in the partial state.

[1] B. Bonet and H. Geffner, "Planning as Heuristic Search," Artificial Intelligence, vol. 129, no. 1, pp. 5–33, Jun. 2001, [https://doi.org/10.1016/S0004-3702(01)00108-4](https://doi.org/10.1016/S0004-3702(01)00108-4).
