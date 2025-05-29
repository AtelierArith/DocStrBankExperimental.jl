```
parse_tree(file_path::String; taxa_to_remove::Union{Array{String,1},Bool}=false)
```

Takes a Nexus file for a tree, returns an internal representation of that tree (and other relevant information).

# Arguments

  * `file_path::String`: file path to the Nexus file.
  * `taxa_to_remove::Union{Array{String,1},Bool}=false`: the taxa that will be removed (if applicable).
