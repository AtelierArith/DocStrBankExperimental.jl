```
mutable struct Trait_Matrix
```

The `Trait_Matrix` is a mutable composite object developed for conducting functional diversity (FD) analyses within the BioExplorer.jl package. It encompasses four key components:

# Fields

  * `traits::Vector{String}`: A vector of strings representing the unique identifiers or names of ecological traits under consideration for analysis.
  * `species::Vector{String}`: A vector of strings signifying the unique identifiers or names of species associated with the ecological traits.
  * `species_data::Array{Any, 2}`: An array of arbitrary data types (`Any`) containing the actual trait data corresponding to each species. This array is structured such that rows correspond to different traits, while columns represent different species.
  * `type::Vector{String}`: A vector of strings indicating the type of traits. Accepted values are "N", "C", or "O", respectively referring to Nominal or Binary traits, Continuous traits, and Ordinal traits.
