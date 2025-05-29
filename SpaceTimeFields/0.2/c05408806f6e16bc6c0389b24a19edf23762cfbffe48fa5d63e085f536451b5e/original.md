```
SpatialGaussian(σx,σy,x0,y0,A[,derivdir=0])
```

Set up a spatial field in the form of a Gaussian centered at `x0,y0` with radii `σx` and `σy` in the respective directions and amplitude `A`. If the optional parameter `deriv` is set to 1 or 2, then it returns the first derivative of a Gaussian in that direction (`x` or `y`, respectively).

`SpatialGaussian(σx,σy,x0,y0,A,u,v[,derivdir=0])` generates a Gaussian that convects at velocity `(u,v)`. It can be evaluated with an additional argument for time.
