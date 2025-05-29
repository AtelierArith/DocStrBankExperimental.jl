```julia
SimpleNoiseProcess{T, N, Tt, T2, T3, ZType, F, F2, inplace, RNGType} <:
AbstractNoiseProcess{T, N, Vector{T2}, inplace}
```

Like `NoiseProcess` but without support for adaptivity. This makes it lightweight and slightly faster.

!!! warn
    `SimpleNoiseProcess` should not be used with adaptive SDE solvers as it will lead to incorrect results.


```julia
SimpleNoiseProcess{iip}(t0, W0, Z0, dist, bridge;
    save_everystep = true,
    rng = Xorshifts.Xoroshiro128Plus(rand(UInt64)),
    reset = true, reseed = true) where {iip}
```

  * `t0` is the first timepoint
  * `W0` is the first value of the process.
  * `Z0` is the first value of the pseudo-process. This is necessary for higher order algorithms. If it's not needed, set to `nothing`.
  * `dist` the distribution for the steps over time.
  * `bridge` the bridging distribution. Optional, but required for adaptivity and interpolating at new values.
  * `save_everystep` whether to save every step of the Brownian timeseries.
  * `rng` the local RNG used for generating the random numbers.
  * `reset` whether to reset the process with each solve.
  * `reseed` whether to reseed the process with each solve.
