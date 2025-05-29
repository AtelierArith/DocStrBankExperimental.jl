```julia
mutable struct DataConfig
```

# Summary

Container to standardize training/testing data configuration.

This container declares if a data configuration has been setup, what the original and complement coded dimensions are, and what the minimums and maximums of the values along each feature dimension are.

# Fields

  * `setup::Bool`: Flag if data has been setup yet or not.

  * `mins::Vector{Float64}`: List of minimum values for each feature.

  * `maxs::Vector{Float64}`: List of maximum values for each feature.

  * `dim::Int64`: Dimensionality of the feature vectors (i.e., number of features).

  * `dim_comp::Int64`: Complement coded feature dimensionality, twice the size of `dim`.
