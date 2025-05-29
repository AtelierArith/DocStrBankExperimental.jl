```julia
set!(
    progn::SpeedyWeather.PrognosticVariables,
    geometry::SpeedyWeather.Geometry;
    u,
    v,
    vor,
    div,
    temp,
    humid,
    pres,
    sea_surface_temperature,
    sea_ice_concentration,
    soil_temperature,
    snow_depth,
    soil_moisture,
    lf,
    add,
    spectral_transform,
    coslat_scaling_included,
    kwargs...
)

```

Sets new values for the keyword arguments (velocities, vorticity, divergence, etc..) into the prognostic variable struct `progn` at timestep index `lf`. If `add==true` they are added to the  current value instead. If a `SpectralTransform` S is provided, it is used when needed to set  the variable, otherwise it is recomputed. In case `u` and `v` are provied, actually the divergence and vorticity are set and `coslat_scaling_included` specficies whether or not the 1/cos(lat)  scaling is already included in the arrays or not (default: `false`)

The input may be:

  * A function or callable object `f(lond, latd, σ) -> value` (multilevel variables)
  * A function or callable object `f(lond, latd) -> value` (surface level variables)
  * An instance of `AbstractGridArray`
  * An instance of `LowerTriangularArray`
  * A scalar `<: Number` (interpreted as a constant field in grid space)
