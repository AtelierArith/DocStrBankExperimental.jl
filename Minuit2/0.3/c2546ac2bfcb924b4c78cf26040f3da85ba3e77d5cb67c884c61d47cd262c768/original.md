```
nmcontour(x, y; cl=0.68, size=50, interpolated=0, ncall=0, iterate=5, use_simplex=true)
```

Get 2D Minos confidence region.

This scans over two parameters and minimises all other free parameters for each scan point. This scan produces a statistical confidence region according to the [profile likelihood method](https://en.wikipedia.org/wiki/Likelihood_function) with a confidence level `cl`, which is asymptotically equal to the coverage probability of the confidence region according to [Wilks' theorem](https://en.wikipedia.org/wiki/Wilks%27_theorem). Note that 1D projections of the 2D confidence region are larger than 1D Minos intervals computed for the same confidence level. This is not an error, but a consequence of Wilks'theorem.

The calculation is expensive since a numerical minimisation has to be performed at various points.

## Arguments

  * `x` : Variable name of the first parameter.
  * `y` : Variable name of the second parameter.
  * `cl::Real=0.68` : Confidence level of the contour. If not set a standard 68 % contour is computed (default). If 0 < cl < 1, the value is interpreted as the confidence level (a probability). For convenience, values cl >= 1 are interpreted as the probability content of a central symmetric interval covering that many standard deviations of a normal distribution.
  * `size::Int=50` : Number of points on the contour to find. Increasing this makes the contour smoother, but requires more computation time.
  * `interpolated::Int=0` : Number of interpolated points on the contour. If you set this to a value larger than size, cubic spline interpolation is used to generate a smoother curve and the interpolated coordinates are returned. Values smaller than size are ignored. Good results can be obtained with size=20, interpolated=200.

## Returns

  * `contour::Vector(Tuple{Float64,Float64})` : Contour points of the form [(x1, y1)...(xn, yn)].
