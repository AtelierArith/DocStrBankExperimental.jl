```
(x, stats) = usymqr(A, b::AbstractVector{FC}, c::AbstractVector{FC};
                    atol::T=√eps(T), rtol::T=√eps(T), itmax::Int=0,
                    timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                    callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(x, stats) = usymqr(A, b, c, x0::AbstractVector; kwargs...)
```

USYMQR can be warm-started from an initial guess `x0` where `kwargs` are the same keyword arguments as above.

USYMQR solves the linear least-squares problem min ‖b - Ax‖² of size m × n. USYMQR solves Ax = b if it is consistent.

USYMQR is based on the orthogonal tridiagonalization process and requires two initial nonzero vectors `b` and `c`. The vector `c` is only used to initialize the process and a default value can be `b` or `Aᴴb` depending on the shape of `A`. The residual norm ‖b - Ax‖ monotonously decreases in USYMQR. When `A` is Hermitian and `b = c`, QMR is equivalent to MINRES. USYMQR is considered as a generalization of MINRES.

It can also be applied to under-determined and over-determined problems. USYMQR finds the minimum-norm solution if problems are inconsistent.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :usymqr`.

For an in-place variant that reuses memory across solves, see [`usymqr!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `m × n`;
  * `b`: a vector of length `m`;
  * `c`: a vector of length `n`.

#### Optional argument

  * `x0`: a vector of length `n` that represents an initial guess of the solution `x`.

#### Keyword arguments

  * `atol`: absolute stopping tolerance based on the residual norm;
  * `rtol`: relative stopping tolerance based on the residual norm;
  * `itmax`: the maximum number of iterations. If `itmax=0`, the default number of iterations is set to `m+n`;
  * `timemax`: the time limit in seconds;
  * `verbose`: additional details can be displayed if verbose mode is enabled (verbose > 0). Information will be displayed every `verbose` iterations;
  * `history`: collect additional statistics on the run such as residual norms, or Aᴴ-residual norms;
  * `callback`: function or functor called as `callback(workspace)` that returns `true` if the Krylov method should terminate, and `false` otherwise;
  * `iostream`: stream to which output is logged.

#### Output arguments

  * `x`: a dense vector of length `n`;
  * `stats`: statistics collected on the run in a [`SimpleStats`](@ref) structure.

#### References

  * M. A. Saunders, H. D. Simon, and E. L. Yip, [*Two Conjugate-Gradient-Type Methods for Unsymmetric Linear Equations*](https://doi.org/10.1137/0725052), SIAM Journal on Numerical Analysis, 25(4), pp. 927–940, 1988.
  * L. Reichel and Q. Ye, [*A generalized LSQR algorithm*](https://doi.org/10.1002/nla.611), Numerical Linear Algebra with Applications, 15(7), pp. 643–660, 2008.
  * A. Buttari, D. Orban, D. Ruiz and D. Titley-Peloquin, [*A tridiagonalization method for symmetric saddle-point and quasi-definite systems*](https://doi.org/10.1137/18M1194900), SIAM Journal on Scientific Computing, 41(5), pp. 409–432, 2019.
  * A. Montoison and D. Orban, [*BiLQ: An Iterative Method for Nonsymmetric Linear Systems with a Quasi-Minimum Error Property*](https://doi.org/10.1137/19M1290991), SIAM Journal on Matrix Analysis and Applications, 41(3), pp. 1145–1166, 2020.
