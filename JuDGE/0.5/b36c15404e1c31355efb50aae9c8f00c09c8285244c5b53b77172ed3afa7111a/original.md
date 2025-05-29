```
tree_from_file(filename::String)
```

Construct tree from a file, each line in the file is of the form B,A,... representing an arc in the tree, from node "A" to node "B". The total number of columns is arbitrary. The first row of the file should be n,p,... these column headers are converted into symbols used to index the `data`. Each column itself converted into a dictionary, indexed by the node.

### Required Arguments

`string` is the full path of the file containing the tree

### Example

```
tree, data = tree_from_file(joinpath(@__DIR__,"tree.csv"))
```
