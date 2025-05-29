```
paint(sample_phase::HaplotypeMosaicPair, panelID::Vector{String},
    refID_to_population::Dict{String, String}, populations::Vector{String})
```

Converts a person's phased haplotype lengths into segments of percentages. This function is used for easier plotting a "painted chromosome".

# Inputs

  * `sample_phase`: A `HaplotypeMosaicPair` storing phase information for a   sample, includes haplotype start position and haplotype label.
  * `panelID`: Sample ID's in the reference haplotype panel
  * `refID_to_population`: A dictionary mapping each sample IDs in the haplotype    reference panel to their population origin. For examples, see output of   [`thousand_genome_population_to_superpopulation`](@ref) and   [`thousand_genome_samples_to_super_population`](@ref)

# Optional inputs

  * `populations`: A unique list of populations present in `refID_to_population`

# Output

  * `s1_composition`: Haplotype 1's composition is stored in `s1_composition[1]`,   which is a list of percentages such that `sum(s1_composition[1]) == 1`. Each   segment `s1_composition[1][i]` has ancestry stored in `s1_composition[2][i]`.
  * `s1_composition`: Haplotype 2's composition is stored in `s2_composition[1]`,   which is a list of percentages such that `sum(s2_composition[1]) == 1`. Each   segment `s2_composition[1][i]` has ancestry stored in `s2_composition[2][i]`.
