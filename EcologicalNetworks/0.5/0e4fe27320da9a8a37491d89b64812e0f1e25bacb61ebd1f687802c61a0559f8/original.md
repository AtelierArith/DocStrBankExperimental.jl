```
dijkstra(N::T) where {T <: DeterministicNetwork}
```

Dijkstra algorithm to return the shortest / easiest paths between all pairs of species in the networks, as long as paths exists. This function will return a tuple, with fields `from`, `to` and `weight`. The number of elements in the tuple is the number of paths. This function works with quantitative and binary networks, and assumes that no interactions are negative.
