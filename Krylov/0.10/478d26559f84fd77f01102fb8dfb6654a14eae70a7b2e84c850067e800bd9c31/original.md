```
(x, stats) = cgne(A, b::AbstractVector{FC};
                  N=I, ldiv::Bool=false,
                  λ::T=zero(T), atol::T=√eps(T),
                  rtol::T=√eps(T), itmax::Int=0,
                  timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                  callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

Solve the consistent linear system

```
Ax + √λs = b
```

of size m × n using the Conjugate Gradient (CG) method, where λ ≥ 0 is a regularization parameter. This method is equivalent to applying CG to the normal equations of the second kind

```
(AAᴴ + λI) y = b
```

but is more stable. When λ = 0, this method solves the minimum-norm problem

min ‖x‖₂  s.t. Ax = b.

When λ > 0, it solves the problem

```
min ‖(x,s)‖₂  s.t. Ax + √λs = b.
```

CGNE produces monotonic errors ‖x-x*‖₂ but not residuals ‖r‖₂. It is formally equivalent to CRAIG, though can be slightly less accurate, but simpler to implement. Only the x-part of the solution is returned.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :cgne`.

For an in-place variant that reuses memory across solves, see [`cgne!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `m × n`;
  * `b`: a vector of length `m`.

#### Keyword arguments

  * `N`: linear operator that models a Hermitian positive-definite matrix of size `n` used for preconditioning;
  * `ldiv`: define whether the preconditioner uses `ldiv!` or `mul!`;
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

#### References

  * J. E. Craig, [*The N-step iteration procedures*](https://doi.org/10.1002/sapm195534164), Journal of Mathematics and Physics, 34(1), pp. 64–73, 1955.
  * J. E. Craig, *Iterations Procedures for Simultaneous Equations*, Ph.D. Thesis, Department of Electrical Engineering, MIT, 1954.
