```
kraken(env::Env, freq=15.0; n_modes=5, range_max=5e3, c_low=0.0, c_high=nothing)
```

Call KRAKEN to compute the propagation of sound waves in an underwater environment.

Required arguments:

  * `env`: underwater environment

Optional keywords:

  * `freq`: frequency (default: 15)
  * `n_modes`: number of modes (default: 5)
  * `range_max`: maximum range (default: 5e3)
  * `c_low`: minimum sound speed (default: 0)
  * `c_high`: maximum sound speed (default: maximum of SSP and SSPHS)
