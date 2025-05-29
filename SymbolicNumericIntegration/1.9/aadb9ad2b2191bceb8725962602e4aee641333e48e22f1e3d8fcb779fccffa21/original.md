```
integrate(eq, x; kwargs...)
```

is the main entry point to integrate a univariate expression `eq` with respect to `x' (optional).

```julia
julia> using Symbolics, SymbolNumericIntegration

julia> @variables x a

julia> integrate(x * sin(2x))
((1//4)*sin(2x) - (1//2)*x*cos(2x), 0, 0)

julia> integrate(x * sin(a * x), x; symbolic = true, detailed = false)
(sin(a*x) - a*x*cos(a*x)) / (a^2)

julia> integrate(x * sin(a * x), (x, 0, 1); symbolic = true, detailed = false)
(sin(a) - a*cos(a)) / (a^2)
```

## Arguments:

  * `eq`: a univariate expression
  * `x`: independent variable (optional if `eq` is univariate) or a tuple of (independent variable, lower bound, upper bound) for definite integration.

## Keyword Arguments:

  * `abstol` (default: `1e-6`): the desired tolerance
  * `num_steps` (default: `2`): the number of different steps with expanding basis to be tried
  * `num_trials` (default: `10`): the number of trials in each step (no changes to the basis)
  * `show_basis` (default: `false`): if true, the basis (list of candidate terms) is printed
  * `bypass` (default: `false`): if true do not integrate terms separately but consider all at once
  * `symbolic` (default: `false`): try symbolic integration first (will be forced if `eq` has symbolic constants)
  * `max_basis` (default: `100`): the maximum number of candidate terms to consider
  * `verbose` (default: `false`): print a detailed report
  * `complex_plane` (default: `true`): generate random test points on the complex plane (if false, the points will be on real axis)
  * `radius` (default: `1.0`): the radius of the disk in the complex plane to generate random test points
  * `opt` (default: `STLSQ(exp.(-10:1:0))`): the sparse regression optimizer (from DataDrivenSparse)
  * `homotopy` (default: `true`): *deprecated*, will be removed in a future version
  * `use_optim` (default: `false`): *deprecated*, will be removed in a future version
  * `detailed` (default: `true`): `(solved, unsolved, err)` output format. If `detailed=false`, only the final integral is returned.

Returns a tuple of (solved, unsolved, err) if `detailed == true`, where

```
solved: the solved integral 
unsolved: the residual unsolved portion of the input
err: the numerical error in reaching the solution
```

Returns the resulting integral or nothing if `detailed == false`
