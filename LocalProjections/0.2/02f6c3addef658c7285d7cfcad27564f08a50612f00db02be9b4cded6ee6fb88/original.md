```
SmoothLP{TS<:ModelSelection, TC<:SearchCriterion} <: AbstractEstimator
```

Smooth local projection method introduced by Barnichon and Brownlees (2019).

The implementation is more computationally efficient than the original Matlab example, as it does not involve explicit construction of the smoother matrix, which can be very large. Regressors that are not B-splines are partialled out before any ridge regression to save computational cost. For selecting the smoothing parameter, the supported criteria are [`LOOCV`](@ref), [`GCV`](@ref) and [`AIC`](@ref).

# Reference

Barnichon, Regis and Christian Brownlees. 2019. "Impulse Response Estimation by Smooth Local Projections." The Review of Economics and Statistics 101 (3): 522-530.
