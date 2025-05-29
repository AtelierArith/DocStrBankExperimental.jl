```
nodes(N)
```

Return all nodes upstream of a node `N`, including `N` itself, in an order consistent with the extended directed acyclic graph of the network. Here "extended" means edges corresponding to training arguments are included.

*Warning.* Not the same as `N.nodes`, which may not include `N`  itself.
