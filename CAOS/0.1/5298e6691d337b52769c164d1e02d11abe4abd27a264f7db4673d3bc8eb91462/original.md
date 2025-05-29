```
classify_new_sequence(tree::Node, character_labels::Dict{String,String}, taxa_labels::Dict{String,String},
sequence_file_path::String, output_directory::String ; all_CA_weights::Dict{Int64,
Dict{String,Int64}}=Dict(1=>Dict("sPu"=>1,"sPr"=>1,"cPu"=>1,"cPr"=>1)), occurrence_weighting::Bool=false,
tiebreaker::Vector{Dict{String,Int64}}=[Dict{String,Int64}()], combo_classification::Bool=false)
```

Takes a tree (Node) and a sequence, and classifies the new sequence using the CAOS tree.

# Arguments

  * `tree::Node`: the tree represented as a Node.
  * `character_labels::Dict{String,String}`: a mapping of the character labels to the corresponding sequences.
  * `taxa_labels::Dict{String,String}`: a mapping of the taxa labels to the character labels.
  * `sequence_file_path::String`: a file path to the sequence to classify.
  * `output_directory::String`: path to the output directory.
  * `all_CA_weights::Dict{Int64,Dict{String,Int64}}=Dict(1=>Dict("sPu"=>1,"sPr"=>1,"cPu"=>1,"cPr"=>1))`: CA weights to be used.
  * `occurrence_weighting::Bool=false`: whether to use occurence weighting in classification.
  * `tiebreaker::Vector{Dict{String,Int64}}=[Dict{String,Int64}()]`: tiebreaker to be used in classification.
  * `combo_classification::Bool=false`: whether to use a combo of Blast and CAOS for classification.
