Diagnostic variables for the particle advection

  * `nparticles::Int64`: Number of particles
  * `nlat_half::Int64`: Number of latitudes on one hemisphere (Eq. incld.), resolution parameter of Grid
  * `locations::Any`: Work array: particle locations
  * `u::Any`: Work array: velocity u
  * `v::Any`: Work array: velocity v
  * `σ_tend::Any`: Work array: velocity w = dσ/dt
  * `interpolator::SpeedyWeather.RingGrids.AnvilInterpolator`: Interpolator to interpolate velocity fields onto particle positions
