```
add_blanks(query_path::String, db_path::String, character_labels::Dict{String,String},
character_labels_no_gaps::Dict{String,String} ; return_blast::Bool=false)
```

Adds blanks to an input sequence given a database.

# Arguments

  * `query_path::String`: path to the query file.
  * `db_path::String`: path to the blast database.
  * `character_labels::Dict{String,String}`: a mapping of the character labels to the corresponding sequences.
  * `character_labels_no_gaps::Dict{String,String}`: character labels with gaps removed from sequences.
  * `return_blast::Bool=false`: whether to return blast results.
  * `protein::Bool=false`: if protein sequence.
