A struct that contains all parameters for the Galewsky et al, 2004 zonal jet intitial conditions for the ShallowWaterModel. Default values as in Galewsky.

  * `latitude::Float64`: jet latitude [˚N]
  * `width::Float64`: jet width [˚], default ≈ 19.29˚
  * `umax::Float64`: jet maximum velocity [m/s]
  * `perturb_lat::Float64`: perturbation latitude [˚N], position in jet by default
  * `perturb_lon::Float64`: perturbation longitude [˚E]
  * `perturb_xwidth::Float64`: perturbation zonal extent [˚], default ≈ 19.1˚
  * `perturb_ywidth::Float64`: perturbation meridinoal extent [˚], default ≈ 3.8˚
  * `perturb_height::Float64`: perturbation amplitude [m]
