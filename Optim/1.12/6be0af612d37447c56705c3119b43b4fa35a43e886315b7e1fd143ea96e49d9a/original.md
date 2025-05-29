# NewtonTrustRegion

## Constructor

```julia
NewtonTrustRegion(; initial_delta = 1.0,
                    delta_hat = 100.0,
                    delta_min = 0.0,
                    eta = 0.1,
                    rho_lower = 0.25,
                    rho_upper = 0.75,
                    use_fg = true)
```

The constructor has 5 keywords:

  * `initial_delta`, the starting trust region radius. Defaults to `1.0`.
  * `delta_hat`, the largest allowable trust region radius. Defaults to `100.0`.
  * `delta_min`, the smallest alowable trust region radius. Optimization halts if the updated radius is smaller than this value. Defaults to `sqrt(eps(Float64))`.
  * `eta`, when `rho` is at least `eta`, accept the step. Defaults to `0.1`.
  * `rho_lower`, when `rho` is less than `rho_lower`, shrink the trust region. Defaults to `0.25`.
  * `rho_upper`, when `rho` is greater than `rho_upper`, grow the trust region. Defaults to `0.75`.
  * `use_fg`, when true always evaluate the gradient with the value after solving the subproblem. This is more efficient if f and g share expensive computations. Defaults to `true`.

## Description

The `NewtonTrustRegion` method implements Newton's method with a trust region for optimizing a function. The method is designed to take advantage of the second-order information in a function's Hessian, but with more stability that Newton's method when functions are not globally well-approximated by a quadratic. This is achieved by repeatedly minimizing quadratic approximations within a dynamically-sized trust region in which the function is assumed to be locally quadratic. See Wright and Nocedal and Wright (ch. 4, 2006) for a discussion of trust-region methods in practice.

## References

  * Nocedal, J., & Wright, S. (2006). Numerical optimization. Springer Science & Business Media.
