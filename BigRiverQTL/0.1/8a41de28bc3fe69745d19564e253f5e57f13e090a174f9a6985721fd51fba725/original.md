`Geno` type contains genotype information for all chromosomes.

  * `sample_id` contains sample names such as genotypes or individual IDs.
  * `chr` contains chromosome names.
  * `marker_name` contains marker names for each chromosome.
  * `val` is a vector of matrices containing allele information in each chromosome. In each matrix, the rows are the samples and the coulmns are the markers.
  * `crosstype` is a field of type `CrossType`. Refer to `CrossType` type for more imformation.
  * `alleles` is a field of type `Alleles`. Refer to `Alleles` type for more imformation.
  * `genotype` is a field of type `Genotype`. Refer to `Genotype` type for more imformation.
  * `genotranspose` is a field of type `GenoTranspose`. Refer to `GenoTranspose` type for more imformation.
