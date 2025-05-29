```
sphMapping( Pos, HSML, Bin_Quant;
            param::mappingParameters,
            kernel::AbstractSPHKernel,
            show_progress::Bool=true,
            parallel::Bool=false,
            reduce_image::Bool=true,
            filter_particles::Bool=true,
            dimensions::Int=2)
```

Maps the data in `Bin_Quant` to a grid. Parameters of mapping are supplied in `param` and the kernel to be used in `kernel`.

# Arguments

  * `Pos`: Matrix (3xNpart) with particle positions.
  * `HSML`: Array with particle hsml.
  * `Bin_Quant`: Array with particle quantity to be mapped.
  * `kernel::AbstractSPHKernel`: Kernel object to be used.
  * `show_progress::Bool=true`: Show progress bar.
  * `parallel::Bool=true`: Run on multiple processors.
  * `reduce_image::Bool=true`: If weights need to be applied or not. Set to `false` for [`part_weight_one`](@ref) and [`part_weight_physical`](@ref).
  * `filter_particles::Bool=true`: Find the particles that are actually contained in the image.
  * `dimensions::Int=2`: Number of mapping dimensions (2 = to grid, 3 = to cube).
