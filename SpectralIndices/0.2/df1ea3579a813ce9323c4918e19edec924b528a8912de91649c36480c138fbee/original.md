```
check_params(index::String, params::Dict, indices::Dict)
```

Check if the parameters dictionary contains all required bands for spectral index computation.

# Arguments

  * `index::String`: The name of the spectral index to check.
  * `params::Dict`: The parameters dictionary to check for required bands.
  * `indices::Dict`: The dictionary containing information about spectral indices.

# Returns

  * `None`

# Examples

```julia
# Check parameters for the NDVI index
index_name = "NDVI"
parameters = Dict("N" => 0.6, "R" => 0.3, "G" => 0.7)
indices = _get_indices()

# Check if parameters contain required bands
check_params(index_name, parameters, indices)
```
