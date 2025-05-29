Start with random vorticity as initial conditions

  * `power::Float64`: [OPTION] Power of the spectral distribution k^power
  * `amplitude::Float64`: [OPTION] the (approximate) amplitude in [1/s], used as standard deviation of spherical harmonic coefficients
  * `max_wavenumber::Int64`: [OPTION] Maximum wavenumber
  * `seed::Int64`: [OPTION] Random number generator seed, 0=randomly seed from Julia's GLOBAL_RNG
  * `random_number_generator::Random.Xoshiro`: Independent random number generator for this random process
