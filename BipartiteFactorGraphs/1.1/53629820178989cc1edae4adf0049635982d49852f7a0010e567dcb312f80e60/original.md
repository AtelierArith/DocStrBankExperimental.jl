```
density(g::BipartiteFactorGraph)
```

Return the density of the graph. 

For bipartite graphs, density is defined as the ratio of the number of  actual edges to the maximum possible number of edges between variable and factor nodes (which is num*variables(g) * num*factors(g)).
