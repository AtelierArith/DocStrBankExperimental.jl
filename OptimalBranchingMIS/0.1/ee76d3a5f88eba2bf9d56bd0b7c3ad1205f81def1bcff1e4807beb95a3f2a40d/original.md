```
counting_mis1(g::SimpleGraph)
```

Calculates the maximum independent set (MIS) for a given `SimpleGraph` by first converting it into an `EliminateGraph` and then applying the `counting_mis1` function.

# Arguments

  * `g::SimpleGraph`: The input graph for which the maximum independent set is to be calculated.

# Returns

  * `MISCount`: The size of the maximum independent set for the provided graph and the count of branches.
