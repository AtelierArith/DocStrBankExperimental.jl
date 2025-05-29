```
(x, stats) = fgmres(A, b::AbstractVector{FC};
                    memory::Int=20, M=I, N=I, ldiv::Bool=false,
                    restart::Bool=false, reorthogonalization::Bool=false,
                    atol::T=√eps(T), rtol::T=√eps(T), itmax::Int=0,
                    timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                    callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(x, stats) = fgmres(A, b, x0::AbstractVector; kwargs...)
```

FGMRES can be warm-started from an initial guess `x0` where `kwargs` are the same keyword arguments as above.

Solve the linear system Ax = b of size n using FGMRES.

FGMRES computes a sequence of approximate solutions with minimum residual. FGMRES is a variant of GMRES that allows changes in the right preconditioner at each iteration.

This implementation allows a left preconditioner M and a flexible right preconditioner N. A situation in which the preconditioner is "not constant" is when a relaxation-type method, a Chebyshev iteration or another Krylov subspace method is used as a preconditioner.  Compared to GMRES, there is no additional cost incurred in the arithmetic but the memory requirement almost doubles. Thus, GMRES is recommended if the right preconditioner N is constant.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :fgmres`.

For an in-place variant that reuses memory across solves, see [`fgmres!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `n`;
  * `b`: a vector of length `n`.

#### Optional argument

  * `x0`: a vector of length `n` that represents an initial guess of the solution `x`.

#### Keyword arguments

  * `memory`: if `restart = true`, the restarted version FGMRES(k) is used with `k = memory`. If `restart = false`, the parameter `memory` should be used as a hint of the number of iterations to limit dynamic memory allocations. Additional storage will be allocated if the number of iterations exceeds `memory`;
  * `M`: linear operator that models a nonsingular matrix of size `n` used for left preconditioning;
  * `N`: linear operator that models a nonsingular matrix of size `n` used for right preconditioning;
  * `ldiv`: define whether the preconditioners use `ldiv!` or `mul!`;
  * `restart`: restart the method after `memory` iterations;
  * `reorthogonalization`: reorthogonalize the new vectors of the Krylov basis against all previous vectors;
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

  * Y. Saad, [*A Flexible Inner-Outer Preconditioned GMRES Algorithm*](https://doi.org/10.1137/0914028), SIAM Journal on Scientific Computing, Vol. 14(2), pp. 461–469, 1993.
