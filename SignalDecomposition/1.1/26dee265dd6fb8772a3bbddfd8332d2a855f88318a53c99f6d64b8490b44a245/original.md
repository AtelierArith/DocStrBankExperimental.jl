```
Fourier([s, ] frequencies, x=true) <: Decomposition
```

Decompose a timeseries `s` into a **sum** `x + r`, by identifying specific `frequencies` at the Fourier space and removing them from the signal. `x` is the removed periodic component while `r` is the residual. If a given frequency is not exactly matching the Fourier frequencies, the closest one is removed.

**Important**: periods/frequencies are defined with respect to the `t` axis length, the actual `t` values are not used in this method. So, frequency `1/12` (a period of `12`) means `12` data points (whose actual value depends on `t`).

If you provide `s` the method plans the forward and inverse Fourier transforms (so that it is efficient to re-use it for `s` of same type and length).

This method works well when a periodic signal P is superimposed on fluctuations S, and you have a good educated guess of what frequencies compose P. This method works well if the given signal has length multiple of the periods given.

There is arbitrarity of which part of the signal `x, r` gets the mean value of `s`, because it is deducted for a better fit. The argument `x=true` attributes it to `x`, use `false` for `r`.
