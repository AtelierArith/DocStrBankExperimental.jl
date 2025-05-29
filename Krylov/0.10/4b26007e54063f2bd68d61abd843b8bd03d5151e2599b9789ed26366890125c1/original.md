```
(x, stats) = cg(A, b::AbstractVector{FC};
                M=I, ldiv::Bool=false, radius::T=zero(T),
                linesearch::Bool=false, atol::T=√eps(T),
                rtol::T=√eps(T), itmax::Int=0,
                timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(x, stats) = cg(A, b, x0::AbstractVector; kwargs...)
```

CG can be warm-started from an initial guess `x0` where `kwargs` are the same keyword arguments as above.

The conjugate gradient method to solve the Hermitian linear system Ax = b of size n.

The method does *not* abort if A is not definite. M also indicates the weighted norm in which residuals are measured.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :cg`.

For an in-place variant that reuses memory across solves, see [`cg!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a Hermitian positive definite matrix of dimension `n`;
  * `b`: a vector of length `n`.

#### Optional argument

  * `x0`: a vector of length `n` that represents an initial guess of the solution `x`.

#### Keyword arguments

  * `M`: linear operator that models a Hermitian positive-definite matrix of size `n` used for centered preconditioning;
  * `ldiv`: define whether the preconditioner uses `ldiv!` or `mul!`;
  * `radius`: add the trust-region constraint ‖x‖ ≤ `radius` if `radius > 0`. Useful to compute a step in a trust-region method for optimization;
  * `linesearch`: if `true`, indicate that the solution is to be used in an inexact Newton method with linesearch. If negative curvature is detected at iteration k > 0, the solution of iteration k-1 is returned. If negative curvature is detected at iteration 0, the right-hand side is returned (i.e., the negative gradient);
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

  * M. R. Hestenes and E. Stiefel, [*Methods of conjugate gradients for solving linear systems*](https://doi.org/10.6028/jres.049.044), Journal of Research of the National Bureau of Standards, 49(6), pp. 409–436, 1952.
