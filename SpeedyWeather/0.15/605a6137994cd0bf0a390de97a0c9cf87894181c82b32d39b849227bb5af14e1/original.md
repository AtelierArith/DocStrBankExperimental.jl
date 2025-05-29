Tendencies of the prognostic variables in spectral and grid-point space

  * `trunc::Int64`
  * `nlat_half::Int64`
  * `nlayers::Int64`
  * `vor_tend::Any`: Vorticity of horizontal wind field [1/s]
  * `div_tend::Any`: Divergence of horizontal wind field [1/s]
  * `temp_tend::Any`: Absolute temperature [K]
  * `humid_tend::Any`: Specific humidity [kg/kg]
  * `u_tend::Any`: Zonal velocity [m/s]
  * `v_tend::Any`: Meridional velocity [m/s]
  * `pres_tend::Any`: Logarithm of surface pressure [Pa]
  * `tracers_tend::Dict{Symbol}`: Tracers [?]
  * `u_tend_grid::Any`: Zonal velocity [m/s], grid
  * `v_tend_grid::Any`: Meridinoal velocity [m/s], grid
  * `temp_tend_grid::Any`: Absolute temperature [K], grid
  * `humid_tend_grid::Any`: Specific humidity [kg/kg], grid
  * `pres_tend_grid::Any`: Logarith of surface pressure [Pa], grid
  * `tracers_tend_grid::Dict{Symbol}`: Tracers [?], grid
