Given a list of citation key groups, create a reference list based on a given CSL and a bibtex bibliography. 

## Arguments

  * `citation_groups::Vector{String}` - a vector of strings containing citation key groups
  * `bibtex_path::String` - path to a bibliography (`.bib` format supported)
  * `csl_path::String` - path a a CSL standard (i.e. `.csl` format)

## Returns

  * String containing an ordered reference list
