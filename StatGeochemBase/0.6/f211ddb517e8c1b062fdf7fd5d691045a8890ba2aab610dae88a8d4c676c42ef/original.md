```julia
normcdf_ll!(mu, sigma, x)
```

Fast log likelihood proportional to the natural logarithm of the cumulative distribution function of a Normal (Gaussian) distribution with mean `mu` and standard deviation `sigma`, evaluated at `x`.

As `normcdf_ll`, but in-place (using `x` as a buffer).
