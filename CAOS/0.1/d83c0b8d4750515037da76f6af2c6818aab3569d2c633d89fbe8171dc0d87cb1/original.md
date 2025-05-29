```
get_nodes(tree::String ; taxa_to_remove::Union{Array{String,1},Bool}=false)
```

Takes a tree in Newick format, returns an internal representation of the tree.

# Arguments

  * `tree::String`: the tree in Newick format.
  * `taxa_to_remove::Union{Array{String,1},Bool}=false`: the taxa that will be removed (if applicable).
