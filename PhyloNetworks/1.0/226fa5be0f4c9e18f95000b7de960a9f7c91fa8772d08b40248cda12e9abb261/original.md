```
getlevel(net, preorder=true, preprocess=false)
```

Level of `net`: maximum number of edges to delete within a biconnected component to make it a tree. If the network is bicombining (each hybrid has 2 parents), then the level is the maximum number of hybrid nodes within a biconnected component. Arguments:

  * `preorder` to direct edges according to the root and store a pre-ordering of nodes in `net.vec_node`, if not done earlier on the network (e.g. after a topology modification)
  * `preprocess` to recalculate & store the biconnected components with [`process_biconnectedcomponents!`](@ref), assuming the preordering was done
