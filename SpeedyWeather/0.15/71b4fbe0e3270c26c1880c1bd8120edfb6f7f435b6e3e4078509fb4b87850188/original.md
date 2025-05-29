Diagnostic variables of the physical parameterizations.

  * `nlat_half::Int64`
  * `ocean::SpeedyWeather.DynamicsVariablesOcean`
  * `land::SpeedyWeather.DynamicsVariablesLand`
  * `precip_large_scale::Any`: Accumulated large-scale precipitation [m]
  * `precip_convection::Any`: Accumulated large-scale precipitation [m]
  * `precip_rate_large_scale::Any`: Rate of large-scale precipitation [m/s], instantaneous
  * `precip_rate_convection::Any`: Rate of large-scale precipitation [m/s], instantaneous
  * `cloud_top::Any`: Cloud top [m]
  * `sensible_heat_flux::Any`: Sensible heat flux [W/m²], positive up
  * `evaporative_flux::Any`: Evaporative flux [kg/s/m^2], positive up
  * `surface_shortwave_up::Any`: Surface radiation: shortwave up [W/m²]
  * `surface_shortwave_down::Any`: Surface radiation: shortwave down [W/m²]
  * `surface_longwave_up::Any`: Surface radiation: longwave up [W/m²]
  * `surface_longwave_down::Any`: Surface radiation: longwave down [W/m²]
  * `outgoing_shortwave_radiation::Any`: Outgoing shortwave radiation [W/m^2]
  * `outgoing_longwave_radiation::Any`: Outgoing longwave radiation [W/m^2]
  * `albedo::Any`: Albedo [1]
  * `cos_zenith::Any`: Cosine of solar zenith angle [1]
