```
unmix_line(line::Int64, reflectance_file::String, mode::String,
            refl_nodata::Float64, refl_scale::Float64,
            normalization::String, library::SpectralLibrary,
            reflectance_uncertainty_file::String="", n_mc::Int64=1,
            combination_type::String="all",
            num_endmembers::Vector{Int64}=[2, 3],
            max_combinations::Int64=-1, optimization="bvls")
```

Unmix a specific line (row of pixels) of reflectance data. See also [`load_line`](@ref), [`unmix_pixel`](@ref).

# Arguments

  * `line::Int64`: Index of the line to unmix.
  * `reflectance_file::String`: Path to the reflectance data.
  * `mode::String`: The mode of unmixing to be used (e.g., "sma", "mesma-best"). See

[`unmix_pixel`](@ref)).

  * `refl_nodata::Float64`: The no data value in the reflectance file.
  * `refl_scale::Float64`: Scaling factor for the reflectance data.
  * `normalization::String`: The normalization method to apply to the reflectance data. See

[`scale_data`](@ref).

  * `library::SpectralLibrary`: Spectral library object containing endmembers for unmixing.
  * `reflectance_uncertainty_file::String`: Optional path to the reflectance uncertainty file.
  * `n_mc::Int64=1`: Number of Monte Carlo iterations to perform.
  * `combination_type::String="all"`: The type of endmember combinations to prepare for

unmixing. See also [`prepare_combinations`](@ref), [`prepare_options`](@ref).

  * `num_endmembers::Vector{Int64}=[2, 3]`: The number of endmembers to consider in

combinations.

  * `max_combinations::Int64=-1`: Maximum number of combinations to consider, defaults to no

limit.

  * `optimization::String`: The optimization method to use (default is "bvls"). See also

[`unmix_pixel`](@ref).

# Returns

  * A tuple containing (see also [`unmix_pixel`](@ref)):

      * The line index.
      * Estimated class fractions for each pixel in the line.
      * A boolean mask of pixels with valid data.
      * Standard deviations of the mixture results (if applicable).
      * Complete fractions for each endmember in the unmixing of each pixel.

# Notes

  * Initializes a random seed for reproducibility.
  * Logs the execution time for unmixing a line.
  * Returns `nothing` if input data is invalid or missing.
