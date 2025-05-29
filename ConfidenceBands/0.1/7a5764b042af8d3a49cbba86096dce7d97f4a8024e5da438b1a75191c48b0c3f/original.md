```
confint(cb::SuptQuantileBootBand, draws::AbstractMatrix; level::Real=0.9, kwargs...)
```

Compute a sup-t confidence band with quantile-based bootstrap implementation based on Montiel Olea and Plagborg-Møller (2019) Algorithm 2. The bootstrap `draws` of point estimates need to be in a matrix with each column being a vector of point estimates from the same draw. In addition to the lower and upper bounds, the pointwise confidence level (when the intervals from the confidence band are viewed as pointwise confidence intervals) is returned as the third object.

The procedure involves solving a root-finding problem for seeking the band with the specified confidence level. This is accomplished with the `find_zero` function from [`Roots.jl`](https://github.com/JuliaMath/Roots.jl). The default bracketing interval (or starting point) used to solve this problem can be overriden by specifying the keyword argument `x0`. A solver from `Roots.jl` can be specified with keyword argument `solver`. Any additional keyword argument will be passed to `find_zero`.

# References

  * Montiel Olea, José Luis and Mikkel Plagborg-Møller. 2019. "Simultaneous Confidence Bands: Theory, Implementation, and an Application to SVARs." Journal of Applied Econometrics 34 (1): 1-17.
