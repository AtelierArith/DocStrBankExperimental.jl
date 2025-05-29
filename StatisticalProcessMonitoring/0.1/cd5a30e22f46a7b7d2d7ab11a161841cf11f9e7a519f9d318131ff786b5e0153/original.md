```
ALT{M}
```

A Generalized Likelihood Ratio statistic for monitoring changes in the variance-covariance matrix.

### Fields

  * `value::Float64`: The value of the statistic, initialized to 0.0.
  * `Ω::M`: The precision matrix of the in-control process.
  * `detΣ::Float64`: The determinant of the in-control process variance.

### References

Alt, F. A. (1984). Multivariate quality control. In N. L. Johnson, S. Kotz, & C. R. Read (Eds.), The encyclopedia of statistical sciences (Vol. 6, pp. 110-122). Wiley.
