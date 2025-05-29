```
sphMapping( Pos::Array{<:Real}, HSML::Array{<:Real}, M::Array{<:Real}, 
            Rho::Array{<:Real}, Bin_Quant::Array{<:Real}, 
            Weights::Array{<:Real}=Rho;
            param::mappingParameters,
            kernel::AbstractSPHKernel,
            show_progress::Bool=true,
            parallel::Bool=false,
            reduce_image::Bool=true,
            return_both_maps::Bool=false,
            filter_particles::Bool=true,
            dimensions::Int=2,
            calc_mean::Bool=false)
```

Maps the data in `Bin_Quant` to a grid. Parameters of mapping are supplied in `param` and the kernel to be used in `kernel`.

# Arguments

  * `Pos`: Matrix (3xNpart) with particle positions
  * `HSML`: Array with particle hsml
  * `M`: Array with particle masses
  * `Rho`: Array with particle densities
  * `Bin_Quant`: Array with particle quantity to be mapped
  * `Weights`: Array with weights. Defaults to density-weighted
  * `param`: `mappingParameters` for this map
  * `kernel`: `AbstractSPHKernel` to be used for mapping
  * `show_progress`: Show progress bar
  * `parallel`: Run on multiple processors
  * `reduce_image`: If weights need to be applied or not. Set to `false` for [`part_weight_physical`](@ref)
  * `return_both_maps`: Returns the full image array. To be used with parallel mapping of subfiles
  * `filter_particles`: Find the particles that are actually contained in the image
  * `dimensions`: Number of mapping dimensions (2 = to grid, 3 = to cube)
  * `calc_mean`: Calculates the mean value along the line of sight. If set to `false` the particle only contributes if its `Bin_Quant` is larger than 0
