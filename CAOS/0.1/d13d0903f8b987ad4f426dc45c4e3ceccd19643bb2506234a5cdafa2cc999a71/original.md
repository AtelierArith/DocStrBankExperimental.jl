```
get_cPu_and_cPr(nodes::Array{Dict{String,Any}}, node_num::Int64, taxa_labels::Dict{String,String},
character_labels::Dict{String,String}, sPu::Array{Dict{String,Any}}, sPr::Array{Dict{String,Any}})
```

Gets all the cPu and cPr for the entire character sequence at a specific node (does not support nucleotide options).

# Arguments

  * `nodes::Array{Dict{String,Any}}`: list of nodes.
  * `node_num::Int64`: current node index.
  * `taxa_labels::Dict{String,String}`: a mapping of the taxa labels to the character labels.
  * `character_labels::Dict{String,String}`: a mapping of the character labels to the corresponding sequences.
  * `sPu::Array{Dict{String,Any}}`: list of simple pure rules.
  * `sPr::Array{Dict{String,Any}}`: list of simple private rules.
