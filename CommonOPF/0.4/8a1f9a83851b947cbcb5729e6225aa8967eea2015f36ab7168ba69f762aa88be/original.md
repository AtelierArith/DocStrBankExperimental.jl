```
splitting_busses(net::Network, source::String; threshold::Int64=10)
```

Determine the busses to split a tree graph on by searching upward from the deepest leafs first and gathering the nearest busses until threshold is met for each subgraph.

Returns a `Vector{String}` for the bus names to split on and `Vector{Vector{String}}` for the  corresponding busses within each sub-graph.

!!! note
    It is not enough to have only the splitting busses to obey the `max_busses` limit because one must also know which sub branches to take from each splitting bus. In other words, we also need all the busses within each subgraph to split properly. For example, if a splitting bus has two sub branches then obeying the max_busses limit can require only including one sub branch out of the splitting bus. To know which branch to take we can use the other busses in the sub graph (which is why this method also returns the bussed in each subgraph).

