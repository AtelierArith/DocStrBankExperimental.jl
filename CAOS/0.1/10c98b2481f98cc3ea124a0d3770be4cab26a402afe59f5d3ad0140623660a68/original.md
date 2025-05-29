```
add_nodes!(tree::Node,sPu::Array{Dict{String,Any}},sPr::Array{Dict{String,Any}},
cPu::Array{Dict{String,Any}},cPr::Array{Dict{String,Any}},taxa_labels::Dict{String,String},
character_labels::Dict{String,String},nodes::Array{Dict{String,Any}},node_num::Int64;complex::Bool=true)
```

Takes a tree (Node), adds all the CA's from the entire tree into the internal representation.

# Arguments

  * `tree::Node`: the tree represented as a Node.
  * `sPu::Array{Dict{String,Any}}`: an array of simple pure rules.
  * `sPr::Array{Dict{String,Any}}`: an array of simple private rules.
  * `cPu::Array{Dict{String,Any}}`: an array of complex pure rules.
  * `cPr::Array{Dict{String,Any}}`: an array of complex private rules.
  * `taxa_labels::Dict{String,String}`: a mapping of the taxa labels to the character labels.
  * `character_labels::Dict{String,String}`: a mapping of the character labels to the corresponding sequences.
  * `nodes::Array{Dict{String,Any}}`: an array of nodes.
  * `node_num::Int64`: the current node number.
  * `complex::Bool=true`: indicates whether complex rules should be calculated
  * `protein::Bool=false`: indicates whether dataset is a protein (or nucleotide)
