```
get_all_neighbors(tree::Node, character_labels::Dict{String,String}, taxa_label::String)
```

Takes a tree (Node) and a taxa label and finds all the neighbors (including duplicates).

# Arguments

  * `tree::Node`: the tree represented as a Node.
  * `character_labels::Dict{String,String}`: character label mappings.
  * `taxa_label::String`: taxa label.
