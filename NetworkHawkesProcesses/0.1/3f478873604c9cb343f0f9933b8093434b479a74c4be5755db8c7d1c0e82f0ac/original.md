```
DiscreteNetworkHawkesProcess(baseline, impulses, weights, adjacency_matrix, network, dt)
```

A discrete network Hawkes process with time step `dt`.

Network Hawkes processes allow for partially-connected networks. The binary `adjacency_matrix` defines network connections generated by the probabilistic `network` model, where `adjacency_matrix[i, j]` represents a connection from node `i` to node `j`.
