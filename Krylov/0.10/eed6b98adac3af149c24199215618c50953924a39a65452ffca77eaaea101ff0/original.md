```
(x, stats) = dqgmres(A, b::AbstractVector{FC};
                     memory::Int=20, M=I, N=I, ldiv::Bool=false,
                     reorthogonalization::Bool=false, atol::T=√eps(T),
                     rtol::T=√eps(T), itmax::Int=0,
                     timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                     callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(x, stats) = dqgmres(A, b, x0::AbstractVector; kwargs...)
```

DQGMRES can be warm-started from an initial guess `x0` where `kwargs` are the same keyword arguments as above.

Solve the consistent linear system Ax = b of size n using DQGMRES.

DQGMRES algorithm is based on the incomplete Arnoldi orthogonalization process and computes a sequence of approximate solutions with the quasi-minimal residual property.

DQGMRES only orthogonalizes the new vectors of the Krylov basis against the `memory` most recent vectors. If MINRES is well defined on `Ax = b` and `memory = 2`, DQGMRES is theoretically equivalent to MINRES. If `k ≤ memory` where `k` is the number of iterations, DQGMRES is theoretically equivalent to GMRES. Otherwise, DQGMRES interpolates between MINRES and GMRES and is similar to MINRES with partial reorthogonalization.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :dqgmres`.

For an in-place variant that reuses memory across solves, see [`dqgmres!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `n`;
  * `b`: a vector of length `n`.

#### Optional argument

  * `x0`: a vector of length `n` that represents an initial guess of the solution `x`.

#### Keyword arguments

  * `memory`: the number of most recent vectors of the Krylov basis against which to orthogonalize a new vector;
  * `M`: linear operator that models a nonsingular matrix of size `n` used for left preconditioning;
  * `N`: linear operator that models a nonsingular matrix of size `n` used for right preconditioning;
  * `reorthogonalization`: reorthogonalize the new vectors of the Krylov basis against the `memory` most recent vectors;
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

#### Reference

  * Y. Saad and K. Wu, [*DQGMRES: a quasi minimal residual algorithm based on incomplete orthogonalization*](https://doi.org/10.1002/(SICI)1099-1506(199607/08)3:4%3C329::AID-NLA86%3E3.0.CO;2-8), Numerical Linear Algebra with Applications, Vol. 3(4), pp. 329–343, 1996.
