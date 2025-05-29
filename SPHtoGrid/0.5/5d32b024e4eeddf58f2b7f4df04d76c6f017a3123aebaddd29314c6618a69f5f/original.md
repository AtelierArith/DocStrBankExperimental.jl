```
healpix_map(Pos, Hsml, M, Rho, Bin_q, Weights;
            center::Vector{<:Real}=[0.0, 0.0, 0.0],
            radius_limits::Vector{<:Real}=[0.0, Inf],
            Nside::Integer=1024,
            kernel::AbstractSPHKernel,
            calc_mean::Bool=true
            show_progress::Bool=true,
            output_from_all_workers::Bool=false)
```

Calculate an allsky map from SPH particles. Returns two `HealpixMap`s: `(image, weight_image)`. To reduce the image afterwards divide `image` by `weight_image`. 

## Arguments:

  * `Pos`: Positions of particles in physical code units
  * `HSML`: hsml of particles in physical code units
  * `M`: Mass of particles in physical code units
  * `Bin_Q`: Quantitiy for binning in arb. units
  * `Weights`: Weights for map
  * `center`: Position from which projection is looking outwards in physical code units
  * `radius_limits`: Inner and outer radius of the shell that should be mapped
  * `Nside`: Nside for healpix map, has to be a power of 2
  * `calc_mean`: Calculate the mean along the line of sight. If set to `false` only particles with `Bin_Q > 0` contribute to the map.
  * `show_progress`: Print a progress bar
  * `output_from_all_workers`: Allow output from multiple workers. If set to false only the main process prints a progress bar.
