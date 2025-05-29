```
function node_age(node<:AbstractNode)::Float64
```

Calculates the age of a node. If the tree is ultrametric then the node age is identical  to the node height. It is calculated by subtracting the path length between the node &  the root from the height of the root. This represents the age of the node, assuming the  leaf farthest from the root has a node age of 0, and the root node is the 'oldest' node.
