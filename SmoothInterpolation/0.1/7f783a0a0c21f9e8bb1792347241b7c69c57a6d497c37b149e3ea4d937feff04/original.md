```
LinearInterpolation(A::SmoothedLinearInterpolation; n_samples = 10)
```

Converting a SmoothedLinearInterpolation object into LinearInterpolation object by sampling the spline sections. The main usage of this is that a LinearInterpolation and especially its integration inverse are much cheaper to evaluate than the  original smoothed equivalents.

Arguments

  * `A`: The SmoothedLinearInterpolation object

## Keyword Arguments

  * `n_samples`: The number of samples per spline section
