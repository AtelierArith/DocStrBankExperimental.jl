```
PointwiseKDE(points::Matrix{T <: Real})
```

Construct a Gaussian KDE from the given matrix of points.

`points` should have size `(ndim, npts)`.  Bandwidth selection is Scott's rule.

The result is a `MultivariateDistribution` object suitable for use with `rand` or `logpdf` or ....
