Forcing term for the Barotropic or ShallowWaterModel with an idealised jet stream similar to the initial conditions from Galewsky, 2004, but mirrored for both hemispheres.

  * `nlat::Int64`: Number of latitude rings
  * `nlayers::Int64`: Number of vertical layers
  * `latitude::Any`: jet latitude [˚N]
  * `width::Any`: jet width [˚], default ≈ 19.29˚
  * `sigma::Any`: sigma level [1], vertical location of jet
  * `speed::Any`: jet speed scale [m/s]
  * `time_scale::Dates.Second`: time scale [days]
  * `amplitude::Vector`: precomputed amplitude vector [m/s²]
  * `tapering::Vector`: precomputed vertical tapering
