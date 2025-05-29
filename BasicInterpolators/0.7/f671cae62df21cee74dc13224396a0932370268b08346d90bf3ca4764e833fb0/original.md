```
ShepardInterpolator(X, y, a=3)
```

Construct a `ShepardInterpolator` for an n-dimensional set of points with coordinates `X` and values `y`. `X` must be an p × N array, where p is the number of points and N is the number of dimensions. `y` must be a length p vector. The value of `a` defines the distance weighting function $r^{-a}$.
