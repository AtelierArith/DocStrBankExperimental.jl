```
(x, stats) = qmr(A, b::AbstractVector{FC};
                 c::AbstractVector{FC}=b, M=I, N=I, ldiv::Bool=false, atol::T=√eps(T),
                 rtol::T=√eps(T), itmax::Int=0, timemax::Float64=Inf, verbose::Int=0,
                 history::Bool=false, callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(x, stats) = qmr(A, b, x0::AbstractVector; kwargs...)
```

QMR can be warm-started from an initial guess `x0` where `kwargs` are the same keyword arguments as above.

Solve the square linear system Ax = b of size n using QMR.

QMR is based on the Lanczos biorthogonalization process and requires two initial vectors `b` and `c`. The relation `bᴴc ≠ 0` must be satisfied and by default `c = b`. When `A` is Hermitian and `b = c`, QMR is equivalent to MINRES. QMR requires support for `adjoint(M)` and `adjoint(N)` if preconditioners are provided.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :qmr`.

For an in-place variant that reuses memory across solves, see [`qmr!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `n`;
  * `b`: a vector of length `n`.

#### Optional argument

  * `x0`: a vector of length `n` that represents an initial guess of the solution `x`.

#### Keyword arguments

  * `c`: the second initial vector of length `n` required by the Lanczos biorthogonalization process;
  * `M`: linear operator that models a nonsingular matrix of size `n` used for left preconditioning;
  * `N`: linear operator that models a nonsingular matrix of size `n` used for right preconditioning;
  * `ldiv`: define whether the preconditioners use `ldiv!` or `mul!`;
  * `atol`: absolute stopping tolerance based on the residual norm;
  * `rtol`: relative stopping tolerance based on the residual norm;
  * `itmax`: the maximum number of iterations. If `itmax=0`, the default number of iterations is set to `2n`;
  * `timemax`: the time limit in seconds;
  * `verbose`: additional details can be displayed if verbose mode is enabled (verbose > 0). Information will be displayed every `verbose` iterations;
  * `history`: collect additional statistics on the run such as residual norms, or Aᴴ-residual norms;
  * `callback`: function or functor called as `callback(workspace)` that returns `true` if the Krylov method should terminate, and `false` otherwise;
  * `iostream`: stream to which output is logged.

#### Output arguments

  * `x`: a dense vector of length `n`;
  * `stats`: statistics collected on the run in a [`SimpleStats`](@ref) structure.

#### References

  * R. W. Freund and N. M. Nachtigal, [*QMR : a quasi-minimal residual method for non-Hermitian linear systems*](https://doi.org/10.1007/BF01385726), Numerische mathematik, Vol. 60(1), pp. 315–339, 1991.
  * R. W. Freund and N. M. Nachtigal, [*An implementation of the QMR method based on coupled two-term recurrences*](https://doi.org/10.1137/0915022), SIAM Journal on Scientific Computing, Vol. 15(2), pp. 313–337, 1994.
  * A. Montoison and D. Orban, [*BiLQ: An Iterative Method for Nonsymmetric Linear Systems with a Quasi-Minimum Error Property*](https://doi.org/10.1137/19M1290991), SIAM Journal on Matrix Analysis and Applications, 41(3), pp. 1145–1166, 2020.
