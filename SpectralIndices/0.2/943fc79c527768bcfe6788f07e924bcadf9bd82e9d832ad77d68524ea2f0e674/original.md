```
load_dataset(dataset::String) -> YAXArray
load_dataset(dataset::String) -> DataFrame
```

Load a specified dataset and convert it into either a YAXArray or a DataFrame, depending on the loaded packages.

# Arguments

  * `dataset::String`: The name of the dataset to load. Currently supports `"sentinel"` and `"spectral"`.

# Returns

  * If YAXArrays is loaded in the namespace, returns a `YAXArray` object containing the loaded dataset, with dimensions labeled as `:x`, `:y`, and `:bands`. The spatial dimensions (`:x` and `:y`) are assumed to have a size of 300 each, and the `:bands` dimension includes ["B02", "B03", "B04", "B08"] bands.
  * If DataFrames is loaded in the namespace, returns a `DataFrame` with the dataset loaded into it.

# Errors

Throws an error if the `dataset` argument does not match one of the predefined dataset names.

# Example

```julia
# Load dataset as YAXArray
yax_ds = SpectralIndices.load_dataset("sentinel")

# Load dataset as DataFrame
df_ds = SpectralIndices.load_dataset("spectral")
```

The current implementation expects the JSON files ("S2_10m.json" for "sentinel" and "spectral.json" for "spectral") to follow a specific format: a vector of vectors where each inner vector represents a band's data in a 300x300 spatial grid for the YAXArray version, or a suitable structure that can be directly converted into a DataFrame for the DataFrame version. The files are already provided for examples in the package in the folder `data`.
