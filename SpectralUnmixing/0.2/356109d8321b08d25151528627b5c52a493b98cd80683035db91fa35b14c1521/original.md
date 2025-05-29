```
unmix_and_write_line(line::Int64, reflectance_file::String, mode::String,
                      refl_nodata::Float64, refl_scale::Float64,
                      normalization::String, library::SpectralLibrary,
                      output_files::Vector{String}, write_complete_fractions::Bool,
                      reflectance_uncertainty_file::String="", n_mc::Int64=1,
                      combination_type::String="all",
                      num_endmembers::Vector{Int64}=[2, 3],
                      max_combinations::Int64=-1, optimization="bvls")
```

Unmix the specified `line` of `reflectance_file` and write the results to `output_files`.

  * Calls [`unmix_line`(@ref)] and [`write_line_results`](@ref), see for arguments.
