```
baypass(data::PopData; filename::Union{String, Nothing} = nothing)
```

Convert a `PopData` object into a Baypass-format matrix. The required input format for the software requires biallelic data. By default, it returns just the Baypass-format matrix; use the keyword argument `filename` to specify a file to write the matrix to. This function **does not perform a Baypass analysis**, but instead creates the input matrix necessary for it.

The matrix specification is:

  * rows = loci

      * each row is a different locus
  * columns = allele counts per population

      * each pair of columns correspond to the alleles' counts (2 alleles, 2 columns) for a population
      * as a result, there should be 2 × n_populations columns
      * e.g. row 1, columns 1:2 are the allele counts for locus 1 in population 1

Baypass information: http://www1.montpellier.inra.fr/CBGP/software/baypass/
