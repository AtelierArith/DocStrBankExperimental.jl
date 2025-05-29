```
gpfitpwm(...)
```

Estimate the GP parameters with the probability weighted moments.

# Implementation

Estimation with the probability weighted moments, as described by [Hosking and Wallis (1987)](https://www.jstor.org/stable/1269343?seq=1), is only possible in the stationary case.

See also [`gpfitpwm`](@ref) for the other methods, [`gpfit`](@ref), [`gpfitbayes`](@ref) and [`ThresholdExceedance`](@ref).

# Reference

Hosking, J. R. M. and Wallis, J. R. (1987). Parameter and quantile estimation for the Generalized Pareto distribution,     *Technometrics*, 29:339-349.
