```julia
normpdf_ll(mu, sigma, x)
```

Fast log likelihood proportional to the natural logarithm of the probability density function of a Normal (Gaussian) distribution with mean `mu` and standard deviation `sigma`, evaluated at `x`.

If `x`, [`mu`, and `sigma`] are given as arrays, the sum of the log likelihood over all `x` will be returned.

See also `normpdf`, `normlogpdf`
