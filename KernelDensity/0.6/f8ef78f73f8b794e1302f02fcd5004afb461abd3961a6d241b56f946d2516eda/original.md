```
kde(data; kwargs...)
kde((xdata, ydata); kwargs...)
```

Kernel density estimation method. Returns 1D or 2D KDE object. The grid used and the values of the estimated density can be obtained from fields `.x` and `.density` respectively. To obtain kde values at points different than the initial grid use the `pdf` method.

The keyword arguments are

  * `boundary`: the lower and upper limits of the kde, tuple in 1D case, tuple of tuples in 2D case,
  * `npoints`: the number of interpolation points to use,
  * `kernel = Normal`: the distributional family from [Distributions.jl](https://github.com/JuliaStats/Distributions.jl),
  * `bandwidth`: the bandwidth of the kernel; default is calculated using Silverman's rule.
