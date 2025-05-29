```
(x, y, stats) = gpmr(A, B, b::AbstractVector{FC}, c::AbstractVector{FC};
                     memory::Int=20, C=I, D=I, E=I, F=I,
                     ldiv::Bool=false, gsp::Bool=false,
                     λ::FC=one(FC), μ::FC=one(FC),
                     reorthogonalization::Bool=false, atol::T=√eps(T),
                     rtol::T=√eps(T), itmax::Int=0,
                     timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                     callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(x, y, stats) = gpmr(A, B, b, c, x0::AbstractVector, y0::AbstractVector; kwargs...)
```

GPMR can be warm-started from initial guesses `x0` and `y0` where `kwargs` are the same keyword arguments as above.

Given matrices `A` of dimension m × n and `B` of dimension n × m, GPMR solves the non-Hermitian partitioned linear system

```
[ λIₘ   A  ] [ x ] = [ b ]
[  B   μIₙ ] [ y ]   [ c ],
```

of size (n+m) × (n+m) where λ and μ are real or complex numbers. `A` can have any shape and `B` has the shape of `Aᴴ`. `A` and `B` must both be nonzero.

This implementation allows left and right block diagonal preconditioners

```
[ C    ] [ λM   A ] [ E    ] [ E⁻¹x ] = [ Cb ]
[    D ] [  B  μN ] [    F ] [ F⁻¹y ]   [ Dc ],
```

and can solve

```
[ λM   A ] [ x ] = [ b ]
[  B  μN ] [ y ]   [ c ]
```

when `CE = M⁻¹` and `DF = N⁻¹`.

By default, GPMR solves unsymmetric linear systems with `λ = 1` and `μ = 1`.

GPMR is based on the orthogonal Hessenberg reduction process and its relations with the block-Arnoldi process. The residual norm ‖rₖ‖ is monotonically decreasing in GPMR.

GPMR stops when `itmax` iterations are reached or when `‖rₖ‖ ≤ atol + ‖r₀‖ * rtol`. `atol` is an absolute tolerance and `rtol` is a relative tolerance.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :gpmr`.

For an in-place variant that reuses memory across solves, see [`gpmr!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `m × n`;
  * `B`: a linear operator that models a matrix of dimension `n × m`;
  * `b`: a vector of length `m`;
  * `c`: a vector of length `n`.

#### Optional arguments

  * `x0`: a vector of length `m` that represents an initial guess of the solution `x`;
  * `y0`: a vector of length `n` that represents an initial guess of the solution `y`.

#### Keyword arguments

  * `memory`: if `restart = true`, the restarted version GPMR(k) is used with `k = memory`. If `restart = false`, the parameter `memory` should be used as a hint of the number of iterations to limit dynamic memory allocations. Additional storage will be allocated if the number of iterations exceeds `memory`;
  * `C`: linear operator that models a nonsingular matrix of size `m`, and represents the first term of the block-diagonal left preconditioner;
  * `D`: linear operator that models a nonsingular matrix of size `n`, and represents the second term of the block-diagonal left preconditioner;
  * `E`: linear operator that models a nonsingular matrix of size `m`, and represents the first term of the block-diagonal right preconditioner;
  * `F`: linear operator that models a nonsingular matrix of size `n`, and represents the second term of the block-diagonal right preconditioner;
  * `ldiv`: define whether the preconditioners use `ldiv!` or `mul!`;
  * `gsp`: if `true`, set `λ = 1` and `μ = 0` for generalized saddle-point systems;
  * `λ` and `μ`: diagonal scaling factors of the partitioned linear system;
  * `reorthogonalization`: reorthogonalize the new vectors of the Krylov basis against all previous vectors;
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

  * A. Montoison and D. Orban, [*GPMR: An Iterative Method for Unsymmetric Partitioned Linear Systems*](https://doi.org/10.1137/21M1459265), SIAM Journal on Matrix Analysis and Applications, 44(1), pp. 293–311, 2023.
