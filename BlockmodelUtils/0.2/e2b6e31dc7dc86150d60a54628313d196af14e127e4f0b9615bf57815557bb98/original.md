```
blockmodel(g, groups; by=identity)
```

Create a `Blockmodel` from `Graphs.AbstractGraph` `g` and vector of group memberships `groups`. The function passed to `by` used to order the groups in the blockmodel.

# Example

```julia using Graphs, BlockmodelUtils

g = erdos_renyi(20, 0.1) gs = rand(['a', 'b'], 20) bm = blockmodel(g, gs)
