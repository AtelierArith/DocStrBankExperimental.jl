```
FFHeuristic()
```

A relaxed planning graph heuristic introduced by the FastForward planner [1].  Similar to [`HSPHeuristic`](@ref), this heuristic precomputes a graph that stores the dependencies between all ground actions and plan-relevant conditions.

To estimate the distance to the goal, a shortest-path search is performed in the graph, starting from the conditions that are true in the current state, and  ending when all the goal conditions are reached. Once a condition is achieved by an action, it is considered to remain true through the rest of the search, hence the relaxed nature of the heuristic. A plan that achieves the goal conditions is reconstructed by following the action back-pointers for each achieved condition, and the cost of this plan is used as the heuristic estimate.

This implementation supports domains with negative preconditions, disjunctive preconditions (i.e., `or`, `exists`), and functional preconditions (e.g. numeric comparisons, or other Boolean-valued functions of non-Boolean fluents). Functional preconditions are handled by (optimistically) assuming they become true once a constituent fluent is modified by some action.

[1] J. Hoffmann, "FF: The Fast-Forward Planning System," AI Magazine, vol. 22, no. 3, pp. 57–57, Sep. 2001, [https://doi.org/10.1609/aimag.v22i3.1572](https://doi.org/10.1609/aimag.v22i3.1572).
