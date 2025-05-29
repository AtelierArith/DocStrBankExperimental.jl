```
read_data_list(path_to_data_or_list::String)
```

The main entry point for reading *.{data,list} files from Philips' MR systems.

This function only really *reads* in the data but does not sort it into, for example, k-spaces.

# Arguments

  * `path_to_data_or_list::String`: The path to the data and list files (without extension).
  * `remove_empty_fields::Bool=true`: If true, remove fields for which there are no samples.

# Returns

  * `samples_per_type::NamedTuple`: A NamedTuple with each field being an array of samples corresponding to one of the types of "complex data vectors" (see `COMPLEX_DATA_VECTOR_TYPES`).
  * `attributes_per_type::NamedTuple`: A NamedTuple with each field being a DataFrame containing attributes corresponding to one of the types of "complex data vectors" (see `COMPLEX_DATA_VECTOR_TYPES`).
  * `info::Vector{String}`: General information about the scan.

# Notes

The .data and .list file should have the same name (except for the extension). The `path` is not required to have an extension since this function will append .data and .list to the path to read the respective files.
