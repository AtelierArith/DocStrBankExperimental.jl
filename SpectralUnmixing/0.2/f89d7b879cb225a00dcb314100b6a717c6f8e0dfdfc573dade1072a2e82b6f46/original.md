```
unmix_pixel(library::SpectralLibrary, img_dat_input::Array{Float64}, unc_dat,
            class_idx, options, mode::String, n_mc::Int64,
            num_endmembers::Vector{Int64}, normalization::String, optimization::String,
            max_combinations::Int64, combination_type::String)
```

Unmix a pixel's spectral data using a given spectral library with options for SMA or MESMA and various Monte Carlo and optimization approaches.

# Arguments

  * `library::SpectralLibrary`: Endmember library for unmixing.
  * `img_dat_input::Array{Float64}`: Spectral data of the pixel.
  * `unc_dat`: An optional array of uncertainty in the pixel spectral data.
  * `class_idx`: A collection of indices indicating class memberships for different

endmembers in `library.spectra`. See also [`prepare_combinations`](@ref), [`prepare_options`](@ref)

  * `options`: A collection of potential endmember combinations for the unmixing process. See

also [`prepare_options`](@ref).

  * `mode::String`: Determines the unmixing approach:

      * `"sma"`: Select endmembers randomly for MC unmixing, returns mean fractions.
      * `"sma-best"`: SMA and output best (lowest cost) MC fraction.
      * `"mesma"`: Evaluate different combinations of endmembers representing each class.
      * `"mesma-best"`: MESMA and output best (lowest cost) MC fraction.
  * `n_mc::Int64`: Number of MC iterations.
  * `num_endmembers::Vector{Int64}`: The number of endmembers to consider.
  * `normalization::String`: The normalization method to apply to the spectral data. See

[`scale_data`](@ref).

  * `optimization::String`: The optimization approach for unmixing: (e.g., `"bvls"`,

`"ldsqp"`, or `"inverse"`). Can optionally contain `"pinv"` or `"qr"` to specify the inverse method, if applicable.

  * `max_combinations::Int64`: Maximum number of combinations to consider.
  * `combination_type::String`: The type of combination (e.g., `"class-even"`). See also

[`prepare_combinations`](@ref), [`prepare_options`](@ref), [`get_sma_permutation`](@ref).

# Returns

  * A tuple containing:

      * `output_mixture::Vector{Float64}`: The estimated fraction of each class in the

    `library`, appended with the brightness.

      * `output_mixture_var::Vector{Float64}`: The variance of each class in the `library`,

    appended with the brightness variance.

      * `output_comp_frac::Vector{Float64}`: The estimated fraction of each endmember in the

    `library`, appended with the brightness.

      * `output_comp_frac_var::Vector{Float64}`: The variance of each endmember in the

    `library`, appended with the brightness variance.
