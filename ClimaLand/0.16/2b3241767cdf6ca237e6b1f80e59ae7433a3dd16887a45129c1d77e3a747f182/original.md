```
clm_canopy_parameters(
    surface_space;
    regridder_type = :InterpolationsRegridder,
    extrapolation_bc = (
        Interpolations.Periodic(),
        Interpolations.Flat(),
        Interpolations.Flat(),
    ),
    lowres=use_lowres_clm(surface_space),
)
```

Reads spatially varying parameters for the canopy, from NetCDF files based on CLM and MODIS data, and regrids them to the grid defined by the `surface_space` of the Clima simulation. Returns a NamedTuple of ClimaCore Fields.

In particular, this file returns a field for

  * clumping index Ω
  * albedo and transmissitivy in PAR and NIR bands
  * leaf angle distribution G function parameter χl
  * Medlyn g1
  * C3 flag
  * VCmax25

The values correspond to the value of the dominant PFT at each point.

The NetCDF files are stored in ClimaArtifacts and more detail on their origin is provided there. The keyword arguments `regridder_type` and `extrapolation_bc` affect the regridding by (1) changing how we interpolate to ClimaCore points which are not in the data, and (2) changing how extrapolate to points beyond the range of the data. The keyword argument lowres is a flag that determines if the 0.9x1.25 or 0.125x0.125 resolution CLM data artifact is used. If the lowres flag is not provided, the clm artifact with the closest resolution to the surface_space is used.
