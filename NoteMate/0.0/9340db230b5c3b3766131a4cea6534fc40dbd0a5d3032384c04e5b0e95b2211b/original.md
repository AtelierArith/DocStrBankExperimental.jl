Given a list of citation key groups, create inline citations based on a given CSL and a bibliography provided in bibtex.

## Arguments

  * `citation_groups::Vector{String}` - a vector of strings containing citation key groups
  * `bibtex_path::String` - path to a bibliography (`.bib` format supported)
  * `csl_path::String` - path a a CSL standard (i.e. `.csl` format)

## Returns

  * Dict with keys as the original citation groups and values as their corresponding inline citation
