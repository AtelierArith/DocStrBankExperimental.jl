```
connect_subgraphs_at_busses(net::Network{SinglePhase}, at_busses::Vector{String}, subgraphs::Vector{Vector})
```

The splitting_busses algorithm does not include over laps in subgraphs. But, we want overlaps at the splitting busses for solving the decomposed branch flow model. So here we add the overlapping splitting busses to each sub graph.
