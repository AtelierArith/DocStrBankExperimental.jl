```
bobyqa(f, x0; kwds...) -> x, info
```

approximately solves the bound constrained optimization problem:

```
min f(x)    subject to   x ∈ Ω ⊆ ℝⁿ
```

with

Ω = { x ∈ ℝⁿ | xl ≤ x ≤ xu }

by M.J.D. Powell's BOBYQA (for "Bounded Optimization BY Quadratic Approximations") method. This algorithm is based on a trust region method where variables are updated according to a quadratic local approximation interpolating the objective function at a number of `npt` points. No derivatives of the objective function are needed.

The arguments are the objective function `f` and the initial variables `x0` which are left unchanged on output. The objective function is called as `f(x)` with `x` the variables, it must implement the following signature:

```
f(x::Vector{Cdouble})::Real
```

The returned result is a 2-tuple `(x, info)` with `x` the variables and `info` a structured object collecting other information provided by the algorithm (see [`PRIMA.Info`](@ref)). If `issuccess(info)` is true, then the algorithm was successful and `x` is an approximate solution of the problem.

Allowed keywords are (`n = length(x)` is the number of variables):

  * `scale` (default value `nothing`) may be set with a vector of `n` positive scaling factors. If specified, the problem is solved in the scaled variables `u ∈ ℝⁿ` such that `u[i] = x[i]/scale[i]`. If unspecified, it is assumed that `scale[i] = 1` for all variables. Note that the objective function, the constraints (linear and non-linear), and the bounds remain specified in the variables. Scaling the variables is useful to improve the conditioning of the problem, to make the scaled variables `u` having approximately the same magnitude, and to adapt to heterogeneous variables or with different units.
  * `rhobeg` (default value `1.0`) is the initial radius of the trust region. The radius of the trust region is given by the Euclidean norm of the scaled variables (see keyword `scale` above).
  * `rhoend` (default value `1.0e-6*rhobeg`) is the final radius of the trust region used to decide whether the algorithm has converged in the scaled variables.
  * `ftarget` (default value `-Inf`) is another convergence setting. The algorithm is stopped as soon as `f(x) ≤ ftarget` and the status `PRIMA.FTARGET_ACHIEVED` is returned.
  * `maxfun` (default `500*n`) is the maximum number of function evaluations allowed for the algorithm. If the number of calls to `f(x)` exceeds this value, the algorithm is stopped and the status `PRIMA.MAXFUN_REACHED` is returned.
  * `iprint` (default value `PRIMA.MSG_NONE`) sets the level of verbosity of the  algorithm. Possible values are `PRIMA.MSG_EXIT`, `PRIMA.MSG_RHO`, or  `PRIMA.MSG_FEVL`. Note that the values that are printed by the software  are those of the scaled variables (see keyword `scale` above).

  * `npt` (default value `2n + 1`) is the number of points used to approximate the local behavior of the objective function and such that `n + 2 ≤ npt ≤ (n + 1)*(n + 2)/2`. The default value corresponds to the one recommended by M.J.D. Powell.

  * `xl` and `xu` (default `fill(+Inf, n)` and `fill(-Inf, n)`) are the elementwise lower and upper bounds for the variables. Feasible variables are such that `xl ≤ x ≤ xu` (elementwise).
