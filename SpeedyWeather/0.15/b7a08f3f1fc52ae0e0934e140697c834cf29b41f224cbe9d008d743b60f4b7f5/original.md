All diagnostic variables.

  * `trunc::Int64`: Spectral resolution: Max degree of spherical harmonics (0-based)
  * `nlat_half::Int64`: Grid resoltion: Number of latitude rings on one hemisphere (Equator incl.)
  * `nlayers::Int64`: Number of vertical layers
  * `nparticles::Int64`: Number of particles for particle advection
  * `tendencies::SpeedyWeather.Tendencies`: Tendencies (spectral and grid) of the prognostic variables
  * `grid::SpeedyWeather.GridVariables`: Gridded prognostic variables
  * `dynamics::SpeedyWeather.DynamicsVariables`: Intermediate variables for the dynamical core
  * `physics::SpeedyWeather.PhysicsVariables`: Global fields returned from physics parameterizations
  * `particles::SpeedyWeather.ParticleVariables{NF, ArrayType, ParticleVector, VectorType, Grid} where {NF, ArrayType, Grid, ParticleVector, VectorType}`: Intermediate variables for the particle advection
  * `column::SpeedyWeather.ColumnVariables`: Vertical column for the physics parameterizations
  * `temp_average::Any`: Average temperature of every horizontal layer [K]
  * `scale::Base.RefValue`: Scale applied to vorticity and divergence
