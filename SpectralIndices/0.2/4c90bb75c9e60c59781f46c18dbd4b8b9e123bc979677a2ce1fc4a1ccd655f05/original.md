```
get_datasets(; datasets=["S2_10m.json", "spectral.json"], data_loc=joinpath(dirname(@__FILE__), "..", "data"))
```

Download predefined datasets from a specified remote location and save them to a local directory.

# Keyword Arguments

  * `datasets::Array{String,1}`: A list of dataset filenames to download. Defaults to `["S2_10m.json", "spectral.json"]`.
  * `data_loc::String`: The local directory path where the downloaded datasets will be saved. Defaults to a `data` directory located one level up from the script's directory.

# Description

This function iterates over a list of dataset filenames, downloads each dataset from a predefined remote URL, and saves them into a specified local directory. The remote URL is currently hardcoded to download specifically the "S2_10m.json" file for any given dataset in the list. Adjust the function or its usage accordingly if different URLs are needed for different datasets.

# Example

```julia
get_datasets()  # Downloads the default datasets to the default location

get_datasets(; datasets=["custom_dataset.json"], data_loc="path/to/custom/directory")
```

This is particularly useful for setting up local environments with necessary data files for further processing or analysis.
