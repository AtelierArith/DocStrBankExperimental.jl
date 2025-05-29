Create a struct that contains all parameters for the Jablonowski and Williamson, 2006 intitial conditions for the primitive equation model. Default values as in Jablonowski.

  * `η₀::Float64`: conversion from σ to Jablonowski's ηᵥ-coordinates
  * `u₀::Float64`: max amplitude of zonal wind [m/s]
  * `perturb_lat::Float64`: perturbation centred at [˚N]
  * `perturb_lon::Float64`: perturbation centred at [˚E]
  * `perturb_uₚ::Float64`: perturbation strength [m/s]
  * `perturb_radius::Float64`: radius of Gaussian perturbation in units of Earth's radius [1]
