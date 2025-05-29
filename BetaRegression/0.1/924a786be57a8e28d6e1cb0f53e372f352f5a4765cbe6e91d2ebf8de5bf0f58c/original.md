```
fit!(b::BetaRegressionModel{T}; maxiter=100, atol=sqrt(eps(T)), rtol=Base.rtoldefault(T))
```

Fit the given [`BetaRegressionModel`](@ref), updating its values in-place. If model convergence is achieved, `b` is returned, otherwise a `ConvergenceException` is thrown.

Fitting the model consists of computing the maximum likelihood estimates for the coefficients and precision parameter via Fisher scoring with analytic derivatives. The model is determined to have converged when the score vector, i.e. the vector of first partial derivatives of the log likelihood with respect to the parameters, is approximately zero. This is determined by `isapprox` using the specified `atol` and `rtol`. `maxiter` dictates the maximum number of Fisher scoring iterations.
