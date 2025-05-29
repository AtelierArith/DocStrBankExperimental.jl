```
save_table(
    output_path::String
    MU::T,
) where T<:WiNDCtable
```

Save a `WiNDCtable` to a file. The file format is HDF5, which can be opened in any other language. The file will have the following structure:

year - DataFrame - The data for each year in the `WiNDCtable` sets - DataFrame - The sets of the `WiNDCtable` columns - Array - The column names of each yearly DataFrame

## Required Arguments

  * `output_path::String`: The path to save the file.
  * `MU::WiNDCtable`: The `WiNDCtable` to save.
