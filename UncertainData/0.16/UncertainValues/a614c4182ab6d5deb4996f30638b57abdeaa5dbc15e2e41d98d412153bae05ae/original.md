```
UncertainScalarKDE(d::KernelDensity.UnivariateKDE, values::AbstractVector{T}, range, pdf)
```

An empirical value represented by a distribution estimated from actual data.

## Fields

  * **`distribution`**: The `UnivariateKDE` estimate for the distribution of `values`.
  * **`values`**: The values from which `distribution` is estimated.
  * **`range`**: The values for which the pdf is estimated.
  * **`pdf`**: The values of the pdf at each point in `range`.
