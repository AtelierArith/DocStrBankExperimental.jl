First-order auto-regressive random process (AR1) in spectral space, evolving `wavenumbers` with respectice `time_scales` and `standard_deviations` independently. Transformed after every time step to grid space with a `clamp` applied to limit extrema. For reproducability `seed` can be provided and an independent `random_number_generator` is used that is reseeded on every `initialize!`. Fields are: 

  * `trunc::Int64`
  * `time_scale::Dates.Second`: [OPTION] Time scale of the AR1 process
  * `wavenumber::Int64`: [OPTION] Wavenumber of the AR1 process
  * `standard_deviation::Any`: [OPTION] Standard deviation of the AR1 process
  * `clamp::Tuple{NF, NF} where NF`: [OPTION] Range to clamp values into after every transform into grid space
  * `seed::Int64`: [OPTION] Random number generator seed, 0=randomly seed from Julia's GLOBAL_RNG
  * `random_number_generator::Random.Xoshiro`: Independent random number generator for this random process
  * `autoregressive_factor::Base.RefValue`: Precomputed auto-regressive factor [1], function of time scale and model time step
  * `noise_factors::Any`: Precomputed noise factors [1] for every total wavenumber l
