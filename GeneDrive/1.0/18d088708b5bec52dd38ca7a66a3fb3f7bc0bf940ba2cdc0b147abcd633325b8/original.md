```
mutable struct Organism{S <: Species}
    gene_data::Genetics
    all_stages::DataStructures.OrderedDict{Type{<:LifeStage}, Stage}
end
```

Generic data container for species-specific genetic and life stage information.

# Arguments

  * `gene_data::Genetics`: Species and modification-specific genetic data.
  * `all_stages::DataStructures.OrderedDict{Type{<:LifeStage}, Stage}`: Dictionary of wildtype species-specific life stage data.
