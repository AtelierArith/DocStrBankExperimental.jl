```
RBMeasurementModel{IPM}(measurement, R2, ny)
```

A measurement model for the Rao-Blackwellized particle filter.

# Fields:

  * `measurement`: The contribution from the nonlinar state to the output, $g$ in $y = g(x^n, u, p, t) + C x^l + e$
  * `R2`: The probability distribution of the measurement noise. If `C == 0`, this may be any distribution, otherwise it must be an instance of `MvNormal` or `SimpleMvNormal`.
  * `ny`: The number of outputs
