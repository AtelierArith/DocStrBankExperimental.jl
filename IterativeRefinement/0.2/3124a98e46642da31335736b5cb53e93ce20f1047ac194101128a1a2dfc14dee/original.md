```
rfldiv(A,b,f=lu; kwargs...) -> x,bnorm,bcomp,flags
```

Compute an accurate solution to a linear system $A x = b$ using extra-precise iterative refinement, with error bounds.

Returns solution `x`, a normwise relative forward error estimate `bnorm`, and maximum componentwise relative error estimate `bcomp`. Specifically,  `bnorm` is an estimate of  $‖xtrue - x‖ / ‖x‖$ (max norms). If the problem is so ill-conditioned that a good solution is unrealizable, `bnorm` and `bcomp` are set to unity (unless `expert`). `flags` contains convergence diagnostics potentially interesting to specialists.

# Arguments

  * `A`: a matrix,
  * `b`: a vector with the same `eltype`,
  * `f`: a factorization function such as `lu`.

## Keywords

  * `DT`: higher-precision type for refinement; defaults to `widen(eltype(A))`
  * `verbosity`: 0(default): quiet, 1: report on iterations, 2: details.
  * `equilibrate::Bool`: whether the function should equilibrate `A` (default `true`).
  * `maxiter`: default 20.
  * `tol`: relative tolerance for convergence, in units of `eps(T)`.
  * `expert::Bool`: whether to return questionable bounds in extreme cases.
  * `κ`: the (max-norm) condition of `A` (see below).
  * `F`: a factorization of `A` (see below).

If `A` has already been equilibrated, and a `Factorization` object `F` and condition estimate `κ` have already been computed, they may be provided as keyword arguments; no check for consistency is done here.

Uses the algorithm of Demmel et al. ACM TOMS, 32, 325 (2006).
