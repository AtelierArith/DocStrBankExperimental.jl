```
admixture_local(tgtfile::String, reffile::String, 
    refID_to_population::Dict{String, String}, populations::Vector{String},
    population_colors::Vector{RGB{FixedPointNumbers.N0f8}})
```

Computes global ancestry estimates for each sample in `tgtfile` using a labeled reference panel `reffile`. 

# Inputs

  * `tgtfile`: VCF or PLINK files. VCF files should end in `.vcf` or `.vcf.gz`.   PLINK files should exclude `.bim/.bed/.fam` trailings but the trio must all   be present in the same directory.
  * `reffile`: Reference haplotype file ending in `.jlso` (compressed binary files).   See [`compress_haplotypes`](@ref).
  * `refID_to_population`: A dictionary mapping each sample IDs in the haplotype    reference panel to their population origin. For examples, see output of   [`thousand_genome_population_to_superpopulation`](@ref) and   [`thousand_genome_samples_to_super_population`](@ref)
  * `population`: A list `String` containing unique populations present in   `values(refID_to_population)`.
  * `population_colors`: A vector of colors for each population.   `typeof(population_colors}` should be `Vector{RGB{FixedPointNumbers.N0f8}}`

# Output

  * `Q`: Matrix containing estimated ancestry fractions. Each row is a haplotype.   Sample 1's haplotypes are in rows 1 and 2, sample 2's are in rows 3, 4...etc.
  * `pop_colors`: Matrix with sample dimension of `Q` storing colors.
