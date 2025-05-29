```
sinusoidal_continuation(T::ClimArray, fs = [1, 2]; Tmin = -Inf, Tmax = Inf)
```

Fill-in the missing values of spatiotemporal field `T`, by fitting sinusoidals to the non-missing values, and then using the fitted sinusoidals for the missing values.

Frequencies are given per year (frequency 2 means 1/2 of a year).

`Tmin, Tmax` limits are used to clamp the result into this range (no clamping in the default case).
