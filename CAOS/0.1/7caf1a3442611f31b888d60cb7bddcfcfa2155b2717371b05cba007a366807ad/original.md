```
remove_from_tree!(tree_tokens::Vector{String}, taxa_to_remove::Union{Array{String,1},Bool})
```

Takes a tree in Newick format, removes a specific taxa from the tree.

# Arguments

  * `tree_tokens::Vector{String}`: the tree in Newick format, tokenized.
  * `taxa_to_remove::Union{Array{String,1},Bool}`: the taxa that will be removed.
