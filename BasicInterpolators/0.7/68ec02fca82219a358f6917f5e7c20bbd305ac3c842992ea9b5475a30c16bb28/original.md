```
BichebyshevInterpolator(x, y, Z)
```

Construct a `BichebyshevInterpolator` for the grid of points defined by coordinates (`x`,`y`) and values `Z`. The given points must lie on a chebyshev grid in each direction. These can be generated with the [`chebygrid`](@ref) function or the interpolator can be constructed directly from a function using the method below.

!!! warning
    The Bichebyshev interpolator is *not thread-safe*. It computes a cosine expansion and does some linear algebra in-place using arrays stored with the object. A single `BichebyshevInterpolator` should never be called by multiple threads at once.

