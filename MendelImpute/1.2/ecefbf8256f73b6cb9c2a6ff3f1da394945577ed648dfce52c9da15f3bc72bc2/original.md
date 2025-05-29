```
convert_compressed(t<:Real, phaseinfo::String, reffile::String)
```

Converts `phaseinfo` into a phased genotype matrix of type `t` using the full reference haplotype panel `H` 

# Inputs

  * `t`: Type of matrix. If `bool`, genotypes are converted to a `BitMatrix`
  * `phaseinfo`: Vector of `HaplotypeMosaicPair`s stored in `.jlso` format
  * `reffile`: The complete (uncompressed) haplotype reference file

# Output

  * `X1`: allele 1 of the phased genotype. Each column is a sample. `X = X1 + X2`.
  * `X2`: allele 2 of the phased genotype. Each column is a sample. `X = X1 + X2`.
  * `phase`: the original data structure after phasing and imputation.
  * `sampleID`: The ID's of each imputed person.
  * `H`: the complete reference haplotype panel. Columns of `H` are haplotypes.
