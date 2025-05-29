```
step!(ds::DiscreteTimeDynamicalSystem [, n::Integer]) → ds
```

Evolve the discrete time dynamical system for 1 or `n` steps.

```
step!(ds::ContinuousTimeDynamicalSystem, [, dt::Real [, stop_at_tdt]]) → ds
```

Evolve the continuous time dynamical system for one integration step.

Alternatively, if a `dt` is given, then progress the integration until there is a temporal difference `≥ dt` (so, step *at least* for `dt` time).

When `true` is passed to the optional third argument, the integration advances for exactly `dt` time.
