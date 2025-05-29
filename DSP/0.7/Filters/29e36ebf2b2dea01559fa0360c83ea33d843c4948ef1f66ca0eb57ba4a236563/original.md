```
filtfilt(coef, x)
```

Filter `x` in the forward and reverse directions using filter coefficients `coef`. The initial state of the filter is computed so that its response to a step function is steady state. Before filtering, the data is extrapolated at both ends with an odd-symmetric extension of length `3*(max(length(b), length(a))-1)`.

Because `filtfilt` applies the given filter twice, the effective filter order is twice the order of `coef`. The resulting signal has zero phase distortion.
