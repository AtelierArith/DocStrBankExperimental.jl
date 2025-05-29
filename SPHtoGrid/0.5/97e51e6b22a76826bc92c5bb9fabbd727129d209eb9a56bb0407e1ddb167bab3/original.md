```
map_it(pos_in, hsml, mass, rho, bin_q, weights, RM=nothing;
       param::mappingParameters,
       kernel::AbstractSPHKernel=WendlandC6(2), 
       snap::Integer=0, 
       units::AbstractString="", 
       image_prefix::String="dummy",
       reduce_image::Bool=true, 
       parallel=true,
       calc_mean::Bool=true, show_progress::Bool=true,
       sort_z::Bool=false,
       stokes::Bool=false,
       projection="xy")
```

Small helper function to copy positions, map particles and save the fits file.

# Arguments

  * `pos_in`: Matrix (3xNpart) with particle positions
  * `hsml`: Array with particle hsml
  * `mass`: Array with particle masses
  * `rho`: Array with particle densities
  * `bin_q`: Array with particle quantity to be mapped
  * `weights`: Array with weights. Defaults to density-weighted
  * `param`: `mappingParameters` for this map
  * `kernel`: `AbstractSPHKernel` to be used for mapping
  * `units`: Unit string will be saved to FITS file
  * `image_prefix`: Name of the file to save, withou `.fits` file-ending
  * `reduce_image`: If weights need to be applied or not. Set to `false` for [`part_weight_physical`](@ref)
  * `parallel`: Run on multiple processors.
  * `calc_mean`: Calculates the mean value along the line of sight. If set to `false` the particle only contributes if its `bin_q` is larger than 0.
  * `show_progress`: Show progress bar
  * `sort_z`: Sort the particles according to their line-of-sight direction. Needed for polarisation mapping.
  * `stokes`: Set to `true` of you are mapping Stokes parameters to account for Faraday rotation of the polarisation angle.
  * `projection`: Which plane the position should be rotated in. Can also be an Array of 3 Euler angles (in [°]) (not used yet!)
