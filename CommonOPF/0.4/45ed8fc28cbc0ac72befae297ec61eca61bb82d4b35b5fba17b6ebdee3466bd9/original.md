```
reduce_tree!(net::Network{SinglePhase})
```

combine any line sets with intermediate busses that have indegree == outdegree == 1 and is not a load bus into a single line

See `remove_bus!` for how the two lines are combined.
