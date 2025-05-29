# Interior-point Newton

## Constructor

```jl
IPNewton(; linesearch::Function = Optim.backtrack_constrained_grad,
         μ0::Union{Symbol,Number} = :auto,
         show_linesearch::Bool = false)
```

The initial barrier penalty coefficient `μ0` can be chosen as a number, or set to `:auto` to let the algorithm decide its value, see `initialize_μ_λ!`.

*Note*: For constrained optimization problems, we recommend always enabling `allow_f_increases` and `successive_f_tol` in the options passed to `optimize`. The default is set to `Optim.Options(allow_f_increases = true, successive_f_tol = 2)`.

As of February 2018, the line search algorithm is specialised for constrained interior-point methods. In future we hope to support more algorithms from `LineSearches.jl`.

## Description

The `IPNewton` method implements an interior-point primal-dual Newton algorithm for solving nonlinear, constrained optimization problems. See Nocedal and Wright (Ch. 19, 2006) for a discussion of interior-point methods for constrained optimization.

## References

The algorithm was [originally written by Tim Holy](https://github.com/JuliaNLSolvers/Optim.jl/pull/303) (@timholy, tim.holy@gmail.com).

  * J Nocedal, SJ Wright (2006), Numerical optimization, second edition. Springer.
  * A Wächter, LT Biegler (2006), On the implementation of an interior-point filter line-search algorithm for large-scale nonlinear programming. Mathematical Programming 106 (1), 25-57.
