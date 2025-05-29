```
bellman_ford(N::T) where {T <: DeterministicNetwork}
```

Bellman-ford algorithm to return the shortest / easiest paths between all pairs of species in the networks, as long as paths exists. This function will return a tuple, with fields `from`, `to` and `weight`. The number of elements in the tuple is the number of paths. This function works with quantitative and binary networks, and assumes that no interactions are negative.

Currently, the Bellman-Ford algorithm is *slower* than the `shortest_path` function, but the arguments are returned in a more usable way. Note that the speed penalty is only valid when measuring the shortest paths in the entire network (and will be fixed relatively soon), and does not apply as much for the shortest paths from a single source node.
