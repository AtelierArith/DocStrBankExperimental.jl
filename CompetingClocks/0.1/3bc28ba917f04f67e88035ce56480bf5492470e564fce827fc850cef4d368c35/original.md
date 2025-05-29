```
enable!(dc::DirectCall, clock::T, distribution::Exponential, when, rng)
```

Tell the `DirectCall` sampler to enable this clock. The `clock` argument is an identifier for the clock. The distribution is a univariate distribution in time. In Julia, distributions are always relative to time `t=0`, but ours start at some absolute enabling time, $t_e$, so we provide that here. The `when` argument is the time at which this clock is enabled, which may be later than when it was first enabled. The `rng` is a random number generator.

If a particular clock had one rate before an event and it has another rate after the event, call `enable!` to update the rate.
