```
get_indices(online::Bool = false)
```

Retrieve the JSON data of spectral indices.

# Arguments

  * `online::Bool = false`: Whether to retrieve the most recent list of indices directly from the GitHub repository (online) or from the local copy (offline).

# Returns

  * `dict`: A dictionary containing the spectral indices data.

# Examples

```julia
# Retrieve the spectral indices from the local copy (offline)
indices = get_indices()

# Retrieve the most recent spectral indices from the online repository
indices = get_indices(true)
'''
```
