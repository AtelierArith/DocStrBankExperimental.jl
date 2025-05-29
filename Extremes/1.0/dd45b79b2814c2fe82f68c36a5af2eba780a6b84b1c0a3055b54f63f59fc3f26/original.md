```
gevfitpwm(...)
```

Estimate the GEV parameters with the probability weighted moments.

# Implementation

Estimation with the probability weighted moments, as described by [Hosking *et al*. (1985)](https://www.tandfonline.com/doi/abs/10.1080/00401706.1985.10488049), is only possible in the stationary case.

See also [`gevfitpwm`](@ref) for the other methods, [`gevfit`](@ref), [`gevfitbayes`](@ref) and [`BlockMaxima`](@ref).

# Reference

Hosking, J. R. M., Wallis, J. R. and Wood, E. F. (1985). Estimation of the generalized extreme-value     distribution by the method of probability-weighted moments. *Technometrics*, 27:251-261.
