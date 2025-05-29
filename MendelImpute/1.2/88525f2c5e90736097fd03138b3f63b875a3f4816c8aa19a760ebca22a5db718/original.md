```
admixture_global(tgtfile::String, reffile::String, 
    refID_to_population::Dict{String, String}, populations::Vector{String})
```

Computes global ancestry estimates for each sample in `tgtfile` using a labeled reference panel `reffile`. 

# Inputs

  * `tgtfile`: VCF or PLINK files. VCF files should end in `.vcf` or `.vcf.gz`.   PLINK files should exclude `.bim/.bed/.fam` trailings but the trio must all   be present in the same directory.
  * `reffile`: Reference haplotype file ending in `.jlso` (compressed binary files).   See [`compress_haplotypes`](@ref).
  * `refID_to_population`: A dictionary mapping each sample IDs in the haplotype    reference panel to their population origin. For examples, see output of   [`thousand_genome_population_to_superpopulation`](@ref) and   [`thousand_genome_samples_to_super_population`](@ref)
  * `populations`: A vector of `String` containing unique populations present in   `values(refID_to_population)`.

# Optional Inputs

  * `Q_outfile`: Output file name for the estimated `Q` matrix. Default   `Q_outfile="mendelimpute.ancestry.Q"`.
  * `imputed_outfile`: Output file name for the imputed genotypes ending in `.jlso`.   Default `impute_outfile = "mendelimpute.ancestry.Q.jlso"`

# Output

  * `Q`: A `DataFrame` containing estimated ancestry fractions. Each row is a sample.   Matrix will be saved in `mendelimpute.ancestry.Q`
