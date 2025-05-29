```
rand_discrete_bn(num_nodes16, max_num_parents=3,
        max_num_states=5, connected=true)
```

Generate a random DiscreteBayesNet.

Creates DiscreteBayesNet with `num_nodes` nodes, with each node having a random number of states and parents, up to `max_num_parents` and `max_num_parents`, respectively. If `connected`, each node (except the first) will be guaranteed at least one parent, making the graph connected.
