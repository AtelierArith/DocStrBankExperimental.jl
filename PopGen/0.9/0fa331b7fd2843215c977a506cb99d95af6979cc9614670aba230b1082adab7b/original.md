# Population genetics analyses in Julia

Repository:    https://www.github.com/biojulia/PopGen.jl/ Documentation: https://biojulia.dev/PopGen.jl/

A few things things you can do to get started:

## Import Data

  * `PopGen.read(filename, kwargs...)`
  * `genepop(infile, kwargs...)`  or similar file-specific importer
  * use available `@gulfsharks` or `@nancycats` datasets

## Explore PopData

  * `populations(PopData)` to view population information
  * `loci(PopData)` to view locus names
  * `samplenames(PopData)` to view sample names
  * `missingdata(PopData, by = ...)` to view missing information

## Manipulate PopData

  * `populations!(PopData, ...)` to rename populations
  * `locations!(PopData, ...)` to add geographical coordinates
  * `exclude!(PopData, kwargs...)` to selectively remove data

## Analyses

  * `richness(PopData)` to calculate allelic richness
  * `Kinship(PopData, method = ...)` to get pairwise Kinship of individuals
  * `summary(PopData)` to calculate F-statistics, heterozygosity, etc.
  * `hwetest(PopData)` to test for Hardy-Weinberg Equilibrium
  * `pairwisefst(PopData)` to calculate FST between pairs of populations
  * `cluster(PopData, kmeans, k = 3)` to perform Kmeans++ clustering
