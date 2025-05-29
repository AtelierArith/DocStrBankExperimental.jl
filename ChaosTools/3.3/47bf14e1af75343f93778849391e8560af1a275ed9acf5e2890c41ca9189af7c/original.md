```
predictability(ds::CoreDynamicalSystem; kwargs...) -> chaos_type, ν, C
```

Determine whether `ds` displays strongly chaotic, partially-predictable chaotic or regular behaviour, using the method by Wernecke et al. described in[^Wernecke2017].

Return the type of the behavior, the cross-distance scaling coefficient `ν` and the correlation coefficient `C`. Typical values for `ν`, `C` and `chaos_type` are given in Table 2 of[^Wernecke2017]:

| `chaos_type` | `ν` | `C` |
| ------------:| ---:| ---:|
|        `:SC` |   0 |   0 |
|       `:PPC` |   0 |   1 |
|       `:REG` |   1 |   1 |

If none of these conditions apply, the return value is `:IND` (for indeterminate).

## Keyword arguments

  * `Ttr = 200`: Extra transient time to evolve the system before sampling from  the trajectory. Should be `Int` for discrete systems.
  * `T_sample = 1e4`: Time to evolve the system for taking samples. Should be `Int` for discrete systems.
  * `n_samples = 500`: Number of samples to take for use in calculating statistics.
  * `λ_max = lyapunov(ds, 5000)`: Value to use for largest Lyapunov exponent for finding the Lyapunov prediction time. If it is less than zero a regular result is returned immediately.
  * `d_tol = 1e-3`: tolerance distance to use for calculating Lyapunov prediction time.
  * `T_multiplier = 10`: Multiplier from the Lyapunov prediction time to the evaluation time.
  * `T_max = Inf`: Maximum time at which to evaluate trajectory distance. If the internally  computed evaluation time is larger than `T_max`, stop at `T_max` instead.  **It is strongly recommended to manually set this!**
  * `δ_range = 10.0 .^ (-9:-6)`: Range of initial condition perturbation distances  to use to determine scaling `ν`.
  * `ν_threshold = C_threshold = 0.5`: Thresholds for scaling coefficients (they become 0 or 1 if they are less or more than the threshold).

## Description

The algorithm samples points from a trajectory of the system to be used as initial conditions. Each of these initial conditions is randomly perturbed by a distance `δ`, and the trajectories for both the original and perturbed initial conditions are evolved up to the 'evaluation time' `T` (see below its definition).

The average (over the samples) distance and cross-correlation coefficient of the state at time `T` is computed. This is repeated for a range of `δ` (defined by `δ_range`), and linear regression is used to determine how the distance and cross-correlation scale with `δ`, allowing for identification of chaos type.

The evaluation time `T` is calculated as `T = T_multiplier*Tλ`, where the Lyapunov prediction time `Tλ = log(d_tol/δ)/λ_max`. This may be very large if the `λ_max` is small, e.g. when the system is regular, so this internally computed time `T` can be overridden by a smaller `T_max` set by the user.

## Performance Notes

For continuous systems, it is likely that the `maxiters` used by the integrators needs to be increased, e.g. to 1e9. This is part of the `diffeq` kwargs. In addition, be aware that this function does a *lot* of internal computations. It is operating in a different speed than e.g. [`lyapunov`](@ref).

[^Wernecke2017]: Wernecke, H., Sándor, B. & Gros, C. *How to test for partially predictable chaos*. [Scientific Reports **7**, (2017)](https://www.nature.com/articles/s41598-017-01083-x).
