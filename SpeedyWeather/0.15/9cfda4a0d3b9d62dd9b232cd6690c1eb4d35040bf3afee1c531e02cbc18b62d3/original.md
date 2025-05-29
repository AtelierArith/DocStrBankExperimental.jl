Transformed prognostic variables (and u, v, temp_virt) into grid-point space.

  * `nlat_half::Int64`
  * `nlayers::Int64`
  * `vor_grid::Any`: Relative vorticity of the horizontal wind [1/s]
  * `div_grid::Any`: Divergence of the horizontal wind [1/s]
  * `temp_grid::Any`: Absolute temperature [K]
  * `temp_virt_grid::Any`: Virtual tempereature [K]
  * `humid_grid::Any`: Specific_humidity [kg/kg]
  * `u_grid::Any`: Zonal velocity [m/s]
  * `v_grid::Any`: Meridional velocity [m/s]
  * `pres_grid::Any`: Logarithm of surface pressure [Pa]
  * `tracers_grid::Dict{Symbol}`: Tracers [?]
  * `random_pattern::Any`: Random pattern controlled by random process [1]
  * `temp_grid_prev::Any`: Absolute temperature [K] at previous time step
  * `humid_grid_prev::Any`: Specific humidity [kg/kg] at previous time step
  * `u_grid_prev::Any`: Zonal velocity [m/s] at previous time step
  * `v_grid_prev::Any`: Meridional velocity [m/s] at previous time step
  * `pres_grid_prev::Any`: Logarithm of surface pressure [Pa] at previous time step
  * `tracers_grid_prev::Dict{Symbol}`: Tracers [?] at previous time step

.
