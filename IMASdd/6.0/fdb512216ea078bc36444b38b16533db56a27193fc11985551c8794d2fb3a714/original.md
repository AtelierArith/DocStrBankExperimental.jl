```
h5merge(output_file::AbstractString, keys_files::Union{AbstractDict{<:AbstractString,<:AbstractString},AbstractVector{<:Pair{<:AbstractString,<:AbstractString}};
      mode::AbstractString="a", skip_existing_entries::Bool=false,
      h5_group_search_depth::Integer=0, h5_strip_group_prefix::Bool=false,
      verbose::Bool=false)
```

Merges multiple files into a single HDF5 output file.

# Arguments

  * `output_file`: Path to the HDF5 file where data will be merged.
  * `keys_files`: A vector or dictionary mapping target group names to input filenames.
  * `mode`: `"w"` to create a new file or `"a"` to append to an existing one.
  * `skip_existing_entries`: If `true`, groups already present in the output file are not overwritten.
  * `h5_group_search_depth`: For input HDF5 files, the depth at which to collect group paths.

      * `0` means use the root (`"/"`).
      * `1` means collect immediate children of the root.
      * Higher values collect groups deeper in the hierarchy.
  * `h5_strip_group_prefix`: If `true`, the target group name (the key from `keys_files`) is omitted from the output HDF5 path. For example, if an input file contains a group path `"/level1/level2"` and the key is `"parent"`, then:

      * With `h5_strip_group_prefix = false`, the output path becomes `"/parent/level1/level2"`.
      * With `h5_strip_group_prefix = true`, the output path becomes `"/level1/level2"`.
  * `verbose`: If `true`, additional logging information is printed.

# Behavior

  * For input files with the `.h5` extension, the function opens the file and collects group paths up to `h5_group_search_depth`. Each collected path is modified by stripping the first N components (using "/" as the delimiter) according to the flag `h5_strip_group_prefix` (if `true`, the parent key is omitted). Then, the corresponding objects are copied into the output file.
  * For other file types (e.g., JSON, YAML, text, markdown), the file is read and stored as text or raw binary data.
  * The function records attributes for each copied group that indicate the original file paths.

Returns a vector of group names (as strings) that were processed.
