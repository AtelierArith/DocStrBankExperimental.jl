```
minimize!(o::VarBayesInfMinimizer, fn::Function, θ0::VecI, Λ0::MatI, x::VecI, y::VecI, Λy::MatI; τ::Real=1e-3, h::Real=0.1, itmax::Int=100)
```

An interface function to proceed the variational Bayesian inference.

## Arguments:

  * `o`:      An object for the minimization created by `minimizer(..., method="variational-inference")`.
  * `fn`:     Objective function to be minimized. `fn` should be callable by `fnc!(y, fn, θ; x)`.            Dispatch the functions `Osnaps.$f(y, fn, θ; x)` where `f = fnc!, jac!, rsd!`.
  * `θ0`:     Initial guess of prior distribution mean.
  * `Λ0`:     Initial guess of prior distribution covariance.
  * `τ`:      A Levenberg-Marquardt method parameters,           pass a smaller number (e.g. 1e-5) when `θ0` is close to the ground truth,           and pass a larger number (e.g. 1e-1) otherwise.
  * `h`:      Step size of finite-difference for computing geodesic acceleration.
  * `itmax`:  Maximum of minimizing iteration (*optional*).
