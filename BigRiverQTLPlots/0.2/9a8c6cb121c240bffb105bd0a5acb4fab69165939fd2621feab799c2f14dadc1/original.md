get*plot*QTL_inputs(vLOD::Vector{<: AbstractFloat}, dfgInfo::DataFrame; 					chrColname::String="Chr", mbColname::String="Mb")

Obtains required inputs to generates a QTL plot.

## Arguments

  * `vLOD` is the vector containing the maximum value of LOD score of each phenotype and its corresponding index.
  * `dfpInfo` is a dataframe containing the phenotype information such as probeset, chromosomes names and Mb distance.
  * `dfgInfo` is a dataframe containing the genotype information such as locus, cM distance, chromosomes names and Mb distance.
  * `chrColname` is the name of the column containing the chromosomes' names, default name is "Chr".
  * `mbColname` is the name of the column containing the megabase DNA length, default name is "Mb".
