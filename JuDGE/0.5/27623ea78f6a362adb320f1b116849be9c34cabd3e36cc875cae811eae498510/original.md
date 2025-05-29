```
capitalcosts(model, expr)
```

Defines a linear expression specifying the capital cost of expansions and shutdowns at the current node

### Required Arguments

`model` is the JuDGE subproblem corresponding to the node in the scenario tree that we are adding specifying the costs for

`expr` is an `AffExpr` which gives the total cost of choosing expansion and shutdown variables at the current node

### Example

```
@capitalcosts(model, sum(expand[i]*cost[node][i] for i in 1:5))
```
