```
(x, stats) = diom(A, b::AbstractVector{FC};
                  memory::Int=20, M=I, N=I, ldiv::Bool=false,
                  reorthogonalization::Bool=false, atol::T=√eps(T),
                  rtol::T=√eps(T), itmax::Int=0,
                  timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                  callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(x, stats) = diom(A, b, x0::AbstractVector; kwargs...)
```

DIOM can be warm-started from an initial guess `x0` where `kwargs` are the same keyword arguments as above.

Solve the consistent linear system Ax = b of size n using DIOM.

DIOM only orthogonalizes the new vectors of the Krylov basis against the `memory` most recent vectors. If CG is well defined on `Ax = b` and `memory = 2`, DIOM is theoretically equivalent to CG. If `k ≤ memory` where `k` is the number of iterations, DIOM is theoretically equivalent to FOM. Otherwise, DIOM interpolates between CG and FOM and is similar to CG with partial reorthogonalization.

An advantage of DIOM is that non-Hermitian or Hermitian indefinite or both non-Hermitian and indefinite systems of linear equations can be handled by this single algorithm.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :diom`.

For an in-place variant that reuses memory across solves, see [`diom!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `n`;
  * `b`: a vector of length `n`.

#### Optional argument

  * `x0`: a vector of length `n` that represents an initial guess of the solution `x`.

#### Keyword arguments

  * `memory`: the number of most recent vectors of the Krylov basis against which to orthogonalize a new vector;
  * `M`: linear operator that models a nonsingular matrix of size `n` used for left preconditioning;
  * `N`: linear operator that models a nonsingular matrix of size `n` used for right preconditioning;
  * `ldiv`: define whether the preconditioners use `ldiv!` or `mul!`;
  * `reorthogonalization`: reorthogonalize the new vectors of the Krylov basis against the `memory` most recent vectors;
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

  * Y. Saad, [*Practical use of some krylov subspace methods for solving indefinite and nonsymmetric linear systems*](https://doi.org/10.1137/0905015), SIAM journal on scientific and statistical computing, 5(1), pp. 203–228, 1984.
