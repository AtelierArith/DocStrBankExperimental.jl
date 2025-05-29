```
tree_from_leaves(leafnodes::Vector{Vector{Int}}, probs::Vector{Float64})
```

Construct tree from Array of leaf nodes, and (optionally) the corresponding probabilities

### Required Arguments

`leafnodes` is an array of arrays defining the set of leaf nodes

### Optional Arguments

`probs` is an array of probabilities for the leaf nodes

### Example

```
(tree,prob) = tree_from_leaves([[1,1,1],[1,1,2],[1,2,1],[1,2,2]],[0.25,0.25,0.25,0.25])
tree = tree_from_leaves([[1,1,1],[1,1,2],[1,2,1],[1,2,2]])
```
