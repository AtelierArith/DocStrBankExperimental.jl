Leapfrog time stepping defined by the following fields

  * `trunc::Int64`: spectral resolution (max degree of spherical harmonics)
  * `nsteps::Int64`: Number of timesteps stored simultaneously in prognostic variables
  * `Δt_at_T31::Dates.Second`: Time step in minutes for T31, scale linearly to `trunc`
  * `radius::AbstractFloat`: Radius of sphere [m], used for scaling
  * `adjust_with_output::Bool`: Adjust Δt*at*T31 with the output*dt to reach output*dt exactly in integer time steps
  * `robert_filter::AbstractFloat`: Robert (1966) time filter coefficeint to suppress comput. mode
  * `williams_filter::AbstractFloat`: Williams time filter (Amezcua 2011) coefficient for 3rd order acc
  * `Δt_millisec::Dates.Millisecond`: time step Δt [ms] at specified resolution
  * `Δt_sec::AbstractFloat`: time step Δt [s] at specified resolution
  * `Δt::AbstractFloat`: time step Δt [s/m] at specified resolution, scaled by 1/radius
