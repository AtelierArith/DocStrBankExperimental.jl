```
SpatialGaussian(Σ::Matrix,x0::Vector,A::Real[,derivdir=0])
```

Set up a spatial field in the form of a Gaussian centered at `x0[1],x0[2]` with covariance matrix `Σ` and amplitude `A`. If the optional parameter `deriv` is set to 1 or 2, then it returns the first derivative of a Gaussian in that direction (`x` or `y`, respectively).
