Convective heating as defined by Lee and Kim, 2003, JAS implemented as convection parameterization. Fields are

  * `nlat::Int64`
  * `time_scale::Dates.Second`: [OPTION] Q*max heating strength as 1K/time*scale
  * `p₀::Any`: [OPTION] Pressure of maximum heating [hPa]
  * `σₚ::Any`: [OPTION] Vertical extent of heating [hPa]
  * `θ₀::Any`: [OPTION] Latitude of heating [˚N]
  * `σθ::Any`: [OPTION] Latitudinal width of heating [˚]
  * `lat_mask::Vector`
