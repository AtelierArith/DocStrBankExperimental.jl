```
(x, stats) = crls(A, b::AbstractVector{FC};
                  M=I, ldiv::Bool=false, radius::T=zero(T),
                  λ::T=zero(T), atol::T=√eps(T), rtol::T=√eps(T),
                  itmax::Int=0, timemax::Float64=Inf,
                  verbose::Int=0, history::Bool=false,
                  callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

Solve the linear least-squares problem

```
minimize ‖b - Ax‖₂² + λ‖x‖₂²
```

of size m × n using the Conjugate Residuals (CR) method. This method is equivalent to applying MINRES to the normal equations

```
(AᴴA + λI) x = Aᴴb.
```

This implementation recurs the residual r := b - Ax.

CRLS produces monotonic residuals ‖r‖₂ and optimality residuals ‖Aᴴr‖₂. It is formally equivalent to LSMR, though can be substantially less accurate, but simpler to implement.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :crls`.

For an in-place variant that reuses memory across solves, see [`crls!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `m × n`;
  * `b`: a vector of length `m`.

#### Keyword arguments

  * `M`: linear operator that models a Hermitian positive-definite matrix of size `n` used for preconditioning;
  * `ldiv`: define whether the preconditioner uses `ldiv!` or `mul!`;
  * `radius`: add the trust-region constraint ‖x‖ ≤ `radius` if `radius > 0`. Useful to compute a step in a trust-region method for optimization;
  * `λ`: regularization parameter;
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

#### Reference

  * D. C.-L. Fong, *Minimum-Residual Methods for Sparse, Least-Squares using Golubg-Kahan Bidiagonalization*, Ph.D. Thesis, Stanford University, 2011.
