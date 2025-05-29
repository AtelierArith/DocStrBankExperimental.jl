```
write_results(output_files::Vector{String}, output_bands::Vector, x_len::Int64,
              y_len::Int64, results, args)
```

Write processed results to specified output ENVI raster files, including primary outputs, uncertainty estimates, and complete fractions, based on the provided parameters.

# Arguments

  * `output_files::Vector{String}`: File paths of the output datasets to be created or

updated. Each entry corresponds to a separate output raster.

  * `output_bands::Vector`: Number of bands for each output dataset. The length of this

vector must match the number of output files.

  * `x_len::Int64`: Width of the output datasets.
  * `y_len::Int64`: Height of the output datasets.
  * `results`: A collection of results, where each result is expected to be a tuple or

similar structure. Specific elements contain the data to be written to the output datasets.

  * `args`: An object or structure containing additional parameters that dictate the

writing behavior. Available options are:     - `args.n_mc`: If greater than 1, an uncertainty output is also written to the second     output file.     - `args.write_complete_fractions`: If set to 1, write complete fractions to the     subsequent output file.

# Notes

  * The primary output is initialized with a no-data value of `-9999` and written to the first output file specified in `output_files`.
  * Each output array is permuted to match the desired dimensions before writing.
