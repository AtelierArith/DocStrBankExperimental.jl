```
Interpolator{T, S, F}
Interpolator(schedule, rate, ceil_fn = x -> ceil(Int, x))
```

A schedule whose output is `schedule(t / rate)` (i.e. it interpolates `schedule(t)`).

This can be useful when your code iterates over real numbers at a fixed rate (e.g. in a fixed time step differential solver), but you want to use a schedule that iterates discretely over integers.

It could also be used to specify `schedule` in units of epochs, while iterating it in units of mini-batches.

Specify `ceil_fn` to apply a ceiling (or flooring) function to `t / rate`.
