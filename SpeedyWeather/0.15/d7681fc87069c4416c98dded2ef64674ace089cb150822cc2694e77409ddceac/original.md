Create a struct that contains all parameters for the Jablonowski and Williamson, 2006 intitial conditions for the primitive equation model. Default values as in Jablonowski.

  * `η₀::Float64`: conversion from σ to Jablonowski's ηᵥ-coordinates
  * `σ_tropopause::Float64`: Sigma coordinates of the tropopause [1]
  * `u₀::Float64`: max amplitude of zonal wind [m/s]
  * `ΔT::Float64`: temperature difference used for stratospheric lapse rate [K], Jablonowski uses ΔT = 4.8e5 [K]
  * `Tmin::Float64`: minimum temperature [K] of profile
