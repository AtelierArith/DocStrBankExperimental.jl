```
graph_cost(estimator::AbstractEstimator, graph::DAG)
```

Get the total estimated cost of the graph. The cost's data type can be chosen by the implementation, but must have a usable lessthan comparison operator (<), basic math operators (+, -) and an implementation of `zero()` and `typemax()`.
