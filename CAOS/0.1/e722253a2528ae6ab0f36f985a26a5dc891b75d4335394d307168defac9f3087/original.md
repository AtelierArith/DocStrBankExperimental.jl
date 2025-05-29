```
get_sPu_and_sPr(nodes::Array{Dict{String,Any}}, node_num::Int64,
taxa_labels::Dict{String,String}, character_labels::Dict{String,String})
```

Gets all the sPu and sPr for the entire character sequence at a specific node.

# Arguments

  * `nodes::Array{Dict{String,Any}}`: list of nodes.
  * `node_num::Int64`: current node index.
  * `taxa_labels::Dict{String,String}`: a mapping of the taxa labels to the character labels.
  * `character_labels::Dict{String,String}`: a mapping of the character labels to the corresponding sequences.
