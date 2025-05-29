```
solve_factoring(missolver, mres::FactoringResult, x::Int) -> (Int, Int)
```

Solve a factoring problem by solving the mapped weighted MIS problem on a unit disk grid graph. It returns (a, b) such that $a  b = x$ holds. `missolver(graph, weights)` should return a vector of integers as the solution.
