```
ongoingcosts(model, expr)
```

Defines a linear expression specifying the ongoing costs of expansions and shutdowns available at the current node

### Required Arguments

`model` is the JuDGE subproblem corresponding to the node in the scenario tree that we are adding specifying the costs for

`expr` is an `AffExpr` which gives the ongoing cost of expansions and shutdowns available at the current node

### Example

```
@ongoingcosts(model, sum(expand[i]*ongoingcosts[node][i] for i in 1:5))
```
