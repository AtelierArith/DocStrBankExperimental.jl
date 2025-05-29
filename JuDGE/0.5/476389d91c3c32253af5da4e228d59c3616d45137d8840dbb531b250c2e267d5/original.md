```
narytree(depth::Int, degree::Int)
```

Given the `depth` and `degree`, this function returns an N-ary tree. Note that a depth of 0 return a single `Leaf` node (which is also the root node of the tree).

### Required Arguments

`depth` is the maximum number of arcs from the root node any `Leaf` node

`degree` is the number of children of all nodes, other than the `Leaf` nodes

### Example

```
tree = narytree(2,2)
```
