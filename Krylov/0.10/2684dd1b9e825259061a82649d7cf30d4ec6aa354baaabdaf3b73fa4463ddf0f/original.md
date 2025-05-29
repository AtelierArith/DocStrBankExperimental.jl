```
(x, stats) = minares(A, b::AbstractVector{FC};
                     M=I, ldiv::Bool=false,
                     λ::T = zero(T), atol::T=√eps(T),
                     rtol::T=√eps(T), Artol::T = √eps(T),
                     itmax::Int=0, timemax::Float64=Inf,
                     verbose::Int=0, history::Bool=false,
                     callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(x, stats) = minares(A, b, x0::AbstractVector; kwargs...)
```

MINARES can be warm-started from an initial guess `x0` where `kwargs` are the same keyword arguments as above.

MINARES solves the Hermitian linear system Ax = b of size n. MINARES minimizes ‖Arₖ‖₂ when M = Iₙ and ‖AMrₖ‖*M otherwise. The estimates computed every iteration are ‖Mrₖ‖₂ and ‖AMrₖ‖*M.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :minares`.

For an in-place variant that reuses memory across solves, see [`minares!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a Hermitian positive definite matrix of dimension `n`;
  * `b`: a vector of length `n`.

#### Optional argument

  * `x0`: a vector of length `n` that represents an initial guess of the solution `x`.

#### Keyword arguments

  * `M`: linear operator that models a Hermitian positive-definite matrix of size `n` used for centered preconditioning;
  * `ldiv`: define whether the preconditioner uses `ldiv!` or `mul!`;
  * `λ`: regularization parameter;
  * `atol`: absolute stopping tolerance based on the residual norm;
  * `rtol`: relative stopping tolerance based on the residual norm;
  * `Artol`: relative stopping tolerance based on the Aᴴ-residual norm;
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

  * A. Montoison, D. Orban and M. A. Saunders, [*MinAres: An Iterative Solver for Symmetric Linear Systems*](https://doi.org/10.1137/23M1605454), SIAM Journal on Matrix Analysis and Applications, 46(1), pp. 509–529, 2025.
