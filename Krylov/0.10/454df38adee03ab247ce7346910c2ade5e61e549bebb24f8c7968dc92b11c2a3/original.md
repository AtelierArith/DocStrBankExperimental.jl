```
(x, y, stats) = trimr(A, b::AbstractVector{FC}, c::AbstractVector{FC};
                      M=I, N=I, ldiv::Bool=false,
                      spd::Bool=false, snd::Bool=false,
                      flip::Bool=false, sp::Bool=false,
                      τ::T=one(T), ν::T=-one(T), atol::T=√eps(T),
                      rtol::T=√eps(T), itmax::Int=0,
                      timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                      callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(x, y, stats) = trimr(A, b, c, x0::AbstractVector, y0::AbstractVector; kwargs...)
```

TriMR can be warm-started from initial guesses `x0` and `y0` where `kwargs` are the same keyword arguments as above.

Given a matrix `A` of dimension m × n, TriMR solves the symmetric linear system

```
[ τE    A ] [ x ] = [ b ]
[  Aᴴ  νF ] [ y ]   [ c ],
```

of size (n+m) × (n+m) where τ and ν are real numbers, E = M⁻¹ ≻ 0, F = N⁻¹ ≻ 0. TriMR handles saddle-point systems (`τ = 0` or `ν = 0`) and adjoint systems (`τ = 0` and `ν = 0`) without any risk of breakdown.

By default, TriMR solves symmetric and quasi-definite linear systems with τ = 1 and ν = -1.

TriMR is based on the preconditioned orthogonal tridiagonalization process and its relation with the preconditioned block-Lanczos process.

```
[ M   0 ]
[ 0   N ]
```

indicates the weighted norm in which residuals are measured. It's the Euclidean norm when `M` and `N` are identity operators.

TriMR stops when `itmax` iterations are reached or when `‖rₖ‖ ≤ atol + ‖r₀‖ * rtol`. `atol` is an absolute tolerance and `rtol` is a relative tolerance.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :trimr`.

For an in-place variant that reuses memory across solves, see [`trimr!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `m × n`;
  * `b`: a vector of length `m`;
  * `c`: a vector of length `n`.

#### Optional arguments

  * `x0`: a vector of length `m` that represents an initial guess of the solution `x`;
  * `y0`: a vector of length `n` that represents an initial guess of the solution `y`.

#### Keyword arguments

  * `M`: linear operator that models a Hermitian positive-definite matrix of size `m` used for centered preconditioning of the partitioned system;
  * `N`: linear operator that models a Hermitian positive-definite matrix of size `n` used for centered preconditioning of the partitioned system;
  * `ldiv`: define whether the preconditioners use `ldiv!` or `mul!`;
  * `spd`: if `true`, set `τ = 1` and `ν = 1` for Hermitian and positive-definite linear system;
  * `snd`: if `true`, set `τ = -1` and `ν = -1` for Hermitian and negative-definite linear systems;
  * `flip`: if `true`, set `τ = -1` and `ν = 1` for another known variant of Hermitian quasi-definite systems;
  * `sp`: if `true`, set `τ = 1` and `ν = 0` for saddle-point systems;
  * `τ` and `ν`: diagonal scaling factors of the partitioned Hermitian linear system;
  * `atol`: absolute stopping tolerance based on the residual norm;
  * `rtol`: relative stopping tolerance based on the residual norm;
  * `itmax`: the maximum number of iterations. If `itmax=0`, the default number of iterations is set to `m+n`;
  * `timemax`: the time limit in seconds;
  * `verbose`: additional details can be displayed if verbose mode is enabled (verbose > 0). Information will be displayed every `verbose` iterations;
  * `history`: collect additional statistics on the run such as residual norms, or Aᴴ-residual norms;
  * `callback`: function or functor called as `callback(workspace)` that returns `true` if the Krylov method should terminate, and `false` otherwise;
  * `iostream`: stream to which output is logged.

#### Output arguments

  * `x`: a dense vector of length `m`;
  * `y`: a dense vector of length `n`;
  * `stats`: statistics collected on the run in a [`SimpleStats`](@ref) structure.

#### Reference

  * A. Montoison and D. Orban, [*TriCG and TriMR: Two Iterative Methods for Symmetric Quasi-Definite Systems*](https://doi.org/10.1137/20M1363030), SIAM Journal on Scientific Computing, 43(4), pp. 2502–2525, 2021.
