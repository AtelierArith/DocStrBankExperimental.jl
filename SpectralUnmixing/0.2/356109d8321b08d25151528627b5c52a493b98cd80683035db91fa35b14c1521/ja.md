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

指定された `line` の `reflectance_file` をアンミックスし、結果を `output_files` に書き込みます。

  * [`unmix_line`(@ref)] と [`write_line_results`](@ref) を呼び出します。引数を参照してください。
