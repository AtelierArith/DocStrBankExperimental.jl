```
get_node(tree::AbstractTree, indices::Vector{Int})
```

Given a `tree`, and an array of `indices`, this function returns the corresponding node in the tree.

### Required Arguments

`tree` is the tree from which we are finding the node

`indicies` is an array of integer indices identifying a node within `tree`.

### Examples

```
node = get_node(tree,[1]) #get the root node
node = get_node(tree,[1,1]) #get the first child of the root node
node = get_node(tree,[1,2]) #get the second child of the root node
```
