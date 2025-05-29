```
renumberconn!(fes::AbstractFESet, new_numbering::AbstractVector{IT}) where {IT<:Integer}
```

Renumber the nodes in the connectivity of the finite elements based on a new numbering for the nodes.

`fes` =finite element set `new_numbering` = new serial numbers for the nodes.  The connectivity           should be changed as `conn[j]` –> `new_numbering[conn[j]]`

Let us say there are nodes not connected to any finite element that we would like to remove from the mesh: here is how that would be accomplished.

```
connected = findunconnnodes(fens, fes);
fens, new_numbering = compactnodes(fens, connected);
fes = renumberconn!(fes, new_numbering);
```

Finally, check that the mesh is valid:

```julia
validate_mesh(fens, fes);
```
