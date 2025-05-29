```
(x, stats) = symmlq(A, b::AbstractVector{FC};
                    M=I, ldiv::Bool=false, window::Int=5,
                    transfer_to_cg::Bool=true, λ::T=zero(T),
                    λest::T=zero(T), etol::T=√eps(T),
                    conlim::T=1/√eps(T), atol::T=√eps(T),
                    rtol::T=√eps(T), itmax::Int=0,
                    timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                    callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(x, stats) = symmlq(A, b, x0::AbstractVector; kwargs...)
```

SYMMLQ can be warm-started from an initial guess `x0` where `kwargs` are the same keyword arguments as above

Solve the shifted linear system

```
(A + λI) x = b
```

of size n using the SYMMLQ method, where λ is a shift parameter, and A is Hermitian.

SYMMLQ produces monotonic errors ‖x* - x‖₂.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :symmlq`.

For an in-place variant that reuses memory across solves, see [`symmlq!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a Hermitian matrix of dimension `n`;
  * `b`: a vector of length `n`.

#### Optional argument

  * `x0`: a vector of length `n` that represents an initial guess of the solution `x`.

#### Keyword arguments

  * `M`: linear operator that models a Hermitian positive-definite matrix of size `n` used for centered preconditioning;
  * `ldiv`: define whether the preconditioner uses `ldiv!` or `mul!`;
  * `window`: number of iterations used to accumulate a lower bound on the error;
  * `transfer_to_cg`: transfer from the SYMMLQ point to the CG point, when it exists. The transfer is based on the residual norm;
  * `λ`: regularization parameter;
  * `λest`: positive strict lower bound on the smallest eigenvalue `λₘᵢₙ` when solving a positive-definite system, such as `λest = (1-10⁻⁷)λₘᵢₙ`;
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
  * `stats`: statistics collected on the run in a [`SymmlqStats`](@ref) structure.

#### Reference

  * C. C. Paige and M. A. Saunders, [*Solution of Sparse Indefinite Systems of Linear Equations*](https://doi.org/10.1137/0712047), SIAM Journal on Numerical Analysis, 12(4), pp. 617–629, 1975.
