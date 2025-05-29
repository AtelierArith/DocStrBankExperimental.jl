```
classify_sequence(sequence::String, tree::Node, CA_weights::Dict{String,Int64},
all_CA_weights::Dict{Int64,Dict{String,Int64}}, occurrence_weighting::Bool,
depth::Int64, tiebreaker::Vector{Dict{String,Int64}} ; blast_results=["Fake Label"], combo_classification::Bool=false, protein::Bool=false)
```

Classifies an input sequence given a phylogentic tree.

# Arguments

  * `sequence::String`: sequence to count matches.
  * `tree::Node`: the tree represented as a Node.
  * `CA_weights::Dict{String,Int64}`: weights to use for CA counts.
  * `all_CA_weights::Dict{Int64,Dict{String,Int64}}`: all sets of weights to use for CA counts.
  * `occurrence_weighting::Bool`: whether to use occurrence weighting during counting.
  * `depth::Int64`: current depth of the tree.
  * `tiebreaker::Vector{Dict{String,Int64}}`: tiebreaking procedures to use.
  * `blast_results=["Fake Label"]`: list of blast results.
  * `combo_classification::Bool=false`: whether to use both Blast and CAOS for classification.
