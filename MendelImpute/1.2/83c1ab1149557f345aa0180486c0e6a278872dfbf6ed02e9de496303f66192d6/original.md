```
composition(sample_phase::HaplotypeMosaicPair, panelID::Vector{String}, 
    refID_to_population::Dict{String, String}, [populations::Vector{String}])
```

Computes a sample's chromosome composition based on phase information. This function is used for easier plotting a person's admixed proportions.

# Inputs

  * `sample_phase`: A `HaplotypeMosaicPair` storing phase information for a   sample, includes haplotype start position and haplotype label.
  * `panelID`: Sample ID's in the reference haplotype panel
  * `refID_to_population`: A dictionary mapping each sample IDs in the haplotype    reference panel to their population origin. For examples, see output of   [`thousand_genome_population_to_superpopulation`](@ref) and   [`thousand_genome_samples_to_super_population`](@ref)

# Optional inputs

  * `populations`: A unique list of populations present in `refID_to_population`

# Output

  * `composition`: A list of percentages where `composition[i]` equals the   sample's ancestry (in %) from `populations[i]`
