```
SpatialGaussian(σ2::Vector,x0::Real,y0::Real,α::Real,A::Real[,derivdir=0])
```

Set up a spatial field in the form of a Gaussian centered at `x0,y0` with variances `σ2[1],σ2[2]` along the orthogonal eigendirections, which are rotated by `α` with respect to the coordinate system; and amplitude `A`. If the optional parameter `deriv` is set to 1 or 2, then it returns the first derivative of a Gaussian in that direction (`x` or `y`, respectively).
