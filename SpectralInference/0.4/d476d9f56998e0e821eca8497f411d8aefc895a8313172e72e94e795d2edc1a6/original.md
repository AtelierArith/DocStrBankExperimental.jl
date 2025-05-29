```
pairedMI_across_treedepth(metacolumns, metacolumns_ids, tree)
pairedMI_across_treedepth(metacolumns, metacolumns_ids, compare::Function=(==), tree::Node; ncuts=100, bootstrap=false, mask=nothing)
```

iterates over each metacolumn and calculates MI between the paired elements of the metacolumn and the paired elements of tree clusters.

Args:

  * metacolumns: column iterator, can be fed to `map(metacolumns)`
  * metacolumn_ids: ids for each element in the metacolumn. should match the leafnames of the tree, but not necessarily the order.
  * tree: NewickTree tree
  * compare: function used to calculate similarity of two elements in metacolumn. Should be written for each element as it will be broadcast across all pairs.

Returns:

  * (; MI, treedepths)
  * MI: Vector{Vector{Float64}} MI for each metacolumn and each tree depth
  * treedepths Vector{<:Number} tree depth (away from root) for each cut of the tree
