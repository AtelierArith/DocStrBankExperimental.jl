```
initialize_surfacevelocitydata(
    raster::Union{String, RasterStack};
    glacier::Union{G, Nothing}=nothing,
    mapping::VM=MeanDateVelocityMapping(),
    compute_vabs_error::Bool=true
) where {G <: AbstractGlacier, VM <: VelocityMapping}
```

Initialize SurfaceVelocityData from Rabatel et. al (2023).

Arguments:

  * `raster::Union{String, RasterStack}`: RasterStack or path of the netCDF file with surface velocity data.
  * `glacier::Union{G, Nothing}`: Glacier associated to the surface velocity datacube.   When provided, the surface velocity data are gridded on the glacier grid using   the `mapping`.
  * `mapping::VM`: Mapping to use in order to grid the data from the coordinates of   the velocity product datacube to the glacier grid.
  * `compute_vabs_error::Bool`: Whether to compute the absolute error uncertainty.
