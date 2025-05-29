```
(X, stats) = block_gmres(A, b::AbstractMatrix{FC};
                         memory::Int=5, M=I, N=I, ldiv::Bool=false,
                         restart::Bool=false, reorthogonalization::Bool=false,
                         atol::T=√eps(T), rtol::T=√eps(T), itmax::Int=0,
                         timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                         callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(X, stats) = block_gmres(A, B, X0::AbstractMatrix; kwargs...)
```

Block-GMRES can be warm-started from an initial guess `X0` where `kwargs` are the same keyword arguments as above.

Solve the linear system AX = B of size n with p right-hand sides using block-GMRES.

#### Interface

To easily switch between block Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :block_gmres`.

For an in-place variant that reuses memory across solves, see [`block_gmres!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `n`;
  * `B`: a matrix of size `n × p`.

#### Optional argument

  * `X0`: a matrix of size `n × p` that represents an initial guess of the solution `X`.

#### Keyword arguments

  * `memory`: if `restart = true`, the restarted version block-GMRES(k) is used with `k = memory`. If `restart = false`, the parameter `memory` should be used as a hint of the number of iterations to limit dynamic memory allocations. Additional storage will be allocated if the number of iterations exceeds `memory`;
  * `M`: linear operator that models a nonsingular matrix of size `n` used for left preconditioning;
  * `N`: linear operator that models a nonsingular matrix of size `n` used for right preconditioning;
  * `ldiv`: define whether the preconditioners use `ldiv!` or `mul!`;
  * `restart`: restart the method after `memory` iterations;
  * `reorthogonalization`: reorthogonalize the new matrices of the block-Krylov basis against all previous matrix;
  * `atol`: absolute stopping tolerance based on the residual norm;
  * `rtol`: relative stopping tolerance based on the residual norm;
  * `itmax`: the maximum number of iterations. If `itmax=0`, the default number of iterations is set to `2 * div(n,p)`;
  * `timemax`: the time limit in seconds;
  * `verbose`: additional details can be displayed if verbose mode is enabled (verbose > 0). Information will be displayed every `verbose` iterations;
  * `history`: collect additional statistics on the run such as residual norms;
  * `callback`: function or functor called as `callback(workspace)` that returns `true` if the block-Krylov method should terminate, and `false` otherwise;
  * `iostream`: stream to which output is logged.

#### Output arguments

  * `X`: a dense matrix of size `n × p`;
  * `stats`: statistics collected on the run in a [`SimpleStats`](@ref) structure.
