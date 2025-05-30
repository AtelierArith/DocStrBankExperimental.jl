```
mutable struct Community_Matrix
```

The `Community_Matrix` is a mutable composite object designed to represent data pertinent to taxonomic diversity (TD) analyses within the BioExplorer.jl package. It comprises four essential components:

# Fields

  * `sites::Vector{String}`: A vector of strings representing the unique identifiers or names of ecological sites or locations where data on species are collected.
  * `species::Vector{String}`: A vector of strings denoting the unique identifiers or names of species observed or recorded within the ecological sites.
  * `species_data::Array{Float32, 2}`: An array of single-precision floating-point numbers (`Float32`) containing the actual data on species occurrences or abundances. This array is structured such that rows correspond to different ecological sites, while columns correspond to different species.
  * `type::String`: A string indicating the type of the data (either 'occurrences' or 'abundances') stored within the object.
