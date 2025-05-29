Start with random velocity as initial conditions

  * `max_speed::Float64`: [OPTION] maximum speed [ms⁻¹]
  * `truncation::Int64`: [OPTION] Maximum wavenumber after truncation
  * `seed::Int64`: [OPTION] Random number generator seed, 0=randomly seed from Julia's GLOBAL_RNG
  * `random_number_generator::Random.Xoshiro`: Independent random number generator for this random process
