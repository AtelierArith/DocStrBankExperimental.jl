```
operation_effect(estimator::AbstractEstimator, graph::DAG, operation::Operation)
```

Get the estimated effect on the cost of the graph, such that `graph_cost(estimator, graph) + operation_effect(estimator, graph, operation) ~= graph_cost(estimator, graph_with_operation_applied)`. There is no hard requirement for this, but the better the estimate, the better an optimization algorithm will be.

!!! note
    There is a default implementation of this function, applying the operation, calling [`graph_cost`](@ref), then popping the operation again.

    It can be much faster to overload this function for a specific estimator and directly compute the effects from the operation if possible.

