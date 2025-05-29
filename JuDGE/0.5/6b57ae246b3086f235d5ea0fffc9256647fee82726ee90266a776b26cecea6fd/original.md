```
resolve_subproblems(judge::JuDGEModel)
```

Once a JuDGE model has converged, it is necessary to re-solve the subproblems to find the optimal decisions within each node.

### Required Arguments

`jmodel` is the JuDGE model that we wish to solve.

### Optional Arguments

`force_match` if true will force all expansion and shutdown variables in the subproblem to exactly match the master problem.

### Examples

```
resolve_subproblems(judge)
```
