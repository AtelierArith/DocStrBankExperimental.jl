```
GaussianKernelSmoother(x,y; leafSize=10)
```

Create a `GaussianKernelSmoother` object of a set of data points with coordinates `x` and values `y`. NB: References to `x` and `y` are stored in the GaussianKernelSmoother object, i.e. if you change `x` or `y` after creating the GaussianKernelSmoother, you will get incorrect results.

See also `smooth`, `density`.
