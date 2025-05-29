```
compactnodes(fens::FENodeSet, connected::Vector{Bool})
```

Compact the finite element node set by deleting unconnected nodes.

`fens` = array of finite element nodes `connected` = The array element `connected[j]` is either 0 (when `j` is an   unconnected node), or a positive number (when node `j` is connected to   other nodes by at least one finite element)

# Output

`fens` = new set of finite element nodes `new_numbering`= array which tells where in the new `fens` array the      connected nodes are (or 0 when the node was unconnected). For instance,      node 5 was connected, and in the new array it is the third node: then      `new_numbering[5]` is 3.

# Examples

Let us say there are nodes not connected to any finite element that you would like to remove from the mesh: here is how that would be accomplished.

```
connected = findunconnnodes(fens, fes);
fens, new_numbering = compactnodes(fens, connected);
fes = renumberconn!(fes, new_numbering);
```

Finally, check that the mesh is valid:

```
validate_mesh(fens, fes);
```
