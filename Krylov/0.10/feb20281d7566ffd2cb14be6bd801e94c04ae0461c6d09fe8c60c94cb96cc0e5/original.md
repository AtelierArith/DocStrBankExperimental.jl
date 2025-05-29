```
(x, stats) = minres(A, b::AbstractVector{FC};
                    M=I, ldiv::Bool=false, window::Int=5,
                    linesearch::Bool=false, λ::T=zero(T), atol::T=√eps(T),
                    rtol::T=√eps(T), etol::T=√eps(T),
                    conlim::T=1/√eps(T), itmax::Int=0,
                    timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                    callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(x, stats) = minres(A, b, x0::AbstractVector; kwargs...)
```

MINRES can be warm-started from an initial guess `x0` where `kwargs` are the same keyword arguments as above.

Solve the shifted linear least-squares problem

```
minimize ‖b - (A + λI)x‖₂²
```

or the shifted linear system

```
(A + λI) x = b
```

of size n using the MINRES method, where λ ≥ 0 is a shift parameter, where A is Hermitian.

MINRES is formally equivalent to applying CR to Ax=b when A is positive definite, but is typically more stable and also applies to the case where A is indefinite.

MINRES produces monotonic residuals ‖r‖₂ and optimality residuals ‖Aᴴr‖₂.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :minres`.

For an in-place variant that reuses memory across solves, see [`minres!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a Hermitian matrix of dimension `n`;
  * `b`: a vector of length `n`.

#### Optional argument

  * `x0`: a vector of length `n` that represents an initial guess of the solution `x`.

#### Keyword arguments

  * `M`: linear operator that models a Hermitian positive-definite matrix of size `n` used for centered preconditioning;
  * `ldiv`: define whether the preconditioner uses `ldiv!` or `mul!`;
  * `window`: number of iterations used to accumulate a lower bound on the error;
  * `linesearch`: if `true`, indicate that the solution is to be used in an inexact Newton method with linesearch. If `linesearch` is true and nonpositive curvature is detected, the solution depends on the iteration: at iteration k = 1, the right-hand side is returned with `workspace.npc_dir` as the preconditioned initial residual; at iteration k > 1, the solution from iteration k-1 is returned with `workspace.npc_dir` as the most recent residual. (Note that the MINRES solver starts at iteration 1, so the first iteration is k = 1);
  * `λ`: regularization parameter;
  * `atol`: absolute stopping tolerance based on the residual norm;
  * `rtol`: relative stopping tolerance based on the residual norm;
  * `etol`: stopping tolerance based on the lower bound on the error;
  * `conlim`: limit on the estimated condition number of `A` beyond which the solution will be abandoned;
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

  * C. C. Paige and M. A. Saunders, [*Solution of Sparse Indefinite Systems of Linear Equations*](https://doi.org/10.1137/0712047), SIAM Journal on Numerical Analysis, 12(4), pp. 617–629, 1975.
  * Y. Liu and F. Roosta, [*MINRES: From Negative Curvature Detection to Monotonicity Properties*](https://doi.org/10.1137/21M143666X), SIAM Journal on Optimization, 32(4), pp. 2636–2661, 2022.
