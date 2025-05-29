```
LagrangeInterpolation(u, t, n = length(t) - 1; extrapolation::ExtrapolationType.T = ExtrapolationType.None, 
extrapolation_left::ExtrapolationType.T = ExtrapolationType.None, extrapolation_right::ExtrapolationType.T = ExtrapolationType.None)
```

It is the method of interpolation using Lagrange polynomials of (k-1)th order passing through all the data points where k is the number of data points.

## Arguments

  * `u`: data points.
  * `t`: time points.
  * `n`: order of the polynomial. Currently only (k-1)th order where k is the number of data points.

## Keyword Arguments

  * `extrapolation`: The extrapolation type applied left and right of the data. Possible options are `ExtrapolationType.None` (default), `ExtrapolationType.Constant`, `ExtrapolationType.Linear` `ExtrapolationType.Extension`, `ExtrapolationType.Periodic` and `ExtrapolationType.Reflective`.
  * `extrapolation_left`: The extrapolation type applied left of the data. See `extrapolation` for the possible options. This keyword is ignored if `extrapolation != Extrapolation.none`.
  * `extrapolation_right`: The extrapolation type applied right of the data. See `extrapolation` for the possible options. This keyword is ignored if `extrapolation != Extrapolation.none`.
