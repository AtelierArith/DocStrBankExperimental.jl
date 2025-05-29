```
(ls::HagerZhangLineSearch)(fg, x₀, η₀, fg₀ = fg(x₀);
                retract = _retract, inner = _inner,
                initialguess = one(fg₀[1]), acceptfirst = false,
                maxiter = ls.maxiter, maxfg = lsmaxfg, verbosity = ls.verbosity)
```

Perform a Hager-Zhang line search to find a step length that satisfies the (approximate) Wolfe conditions.

## Arguments:

  * `ls::HagerZhangLineSearch`: The HagerZhangLineSearch object.
  * `fg`: Function that computes the objective function and its gradient.
  * `x₀`: Starting point.
  * `η₀`: Search direction.
  * `fg₀`: Objective function and gradient evaluated at `x₀`. Defaults to `fg(x₀)`, but can be supplied if this information has already been calculated.

## Keyword Arguments:

  * `retract`: Function that performs the retraction step, i.e. the generalisation of `x₀ + α * η₀`. Defaults to `_retract`.
  * `inner`: Function that computes the inner product between search direction and gradient. Defaults to `_inner`.
  * `initialguess::Real`: Initial guess for the step length. Defaults to `one(fg₀[1])`.
  * `acceptfirst::Bool`: Parameter that controls whether the initial guess can be accepted if it satisfies the strong Wolfe conditions. Defaults to `false`, thus requiring  at least one line search iteration and one extra function evaluation.
  * `maxiter::Int`: Hard limit on the number of iterations. Default is `50`.
  * `maxfg::Int`: Soft limit on the number of function evaluations. Default is `100`.
  * `verbosity::Int`: The verbosity level (see below). Default is `0`.

### Verbosity Levels

  * `0`: No output.
  * `1`: Single output about convergence when the linesearch has terminated.
  * `2`: Output after the start and every individual iteration step of the Hager-Zhang linesearch.
  * `3`: Additional output about the initial bracketing and further bracket update and bisection steps.
  * `4`: Output after every function evaluation in the bracketing, updating, and bisection steps.

## Returns:

  * `x`: The point `retract(x₀, η₀, α)` where the (approximate) Wolfe conditions are satisfied.
  * `f`: Function value at `x`.
  * `g`: Gradient at `x`.
  * `ξ`: Tangent at `x` to the line search path.
  * `α`: Step length that satisfies the (approximate) Wolfe conditions.
  * `numfg`: Number of function evaluations performed.
