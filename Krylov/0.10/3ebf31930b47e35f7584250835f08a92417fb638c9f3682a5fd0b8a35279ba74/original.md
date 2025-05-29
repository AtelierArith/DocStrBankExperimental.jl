```
(x, stats) = cgls_lanczos_shift(A, b::AbstractVector{FC}, shifts::AbstractVector{T};
                                M=I, λ::T=zero(T), atol::T=√eps(T), rtol::T=√eps(T),
                                radius::T=zero(T), itmax::Int=0, verbose::Int=0,
                                history::Bool=false, callback=workspace->false,
                                iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

Solve the regularized linear least-squares problem

```
minimize ‖b - Ax‖₂² + λ‖x‖₂²
```

using the Conjugate Gradient (CG) method, where λ ≥ 0 is a regularization parameter. This method is equivalent to applying CG to the normal equations

```
(AᴴA + λI) x = Aᴴb
```

but is more stable.

CGLS produces monotonic residuals ‖r‖₂ but not optimality residuals ‖Aᴴr‖₂. It is formally equivalent to LSQR, though can be slightly less accurate, but simpler to implement.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :cgls_lanczos_shift`.

For an in-place variant that reuses memory across solves, see [`cgls_lanczos_shift!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `m × n`;
  * `b`: a vector of length `m`;
  * `shifts`: a vector of length `p`.

#### Keyword arguments

  * `M`: linear operator that models a Hermitian positive-definite matrix of size `n` used for preconditioning;
  * `ldiv`: define whether the preconditioner uses `ldiv!` or `mul!`;
  * `atol`: absolute stopping tolerance based on the residual norm;
  * `rtol`: relative stopping tolerance based on the residual norm;
  * `itmax`: the maximum number of iterations. If `itmax=0`, the default number of iterations is set to `m+n`;
  * `timemax`: the time limit in seconds;
  * `verbose`: additional details can be displayed if verbose mode is enabled (verbose > 0). Information will be displayed every `verbose` iterations;
  * `history`: collect additional statistics on the run such as residual norms, or Aᴴ-residual norms;
  * `callback`: function or functor called as `callback(workspace)` that returns `true` if the Krylov method should terminate, and `false` otherwise;
  * `iostream`: stream to which output is logged.

#### Output arguments

  * `x`: a vector of `p` dense vectors, each one of length `n`;
  * `stats`: statistics collected on the run in a [`LanczosShiftStats`](@ref) structure.

#### References

  * M. R. Hestenes and E. Stiefel. [*Methods of conjugate gradients for solving linear systems*](https://doi.org/10.6028/jres.049.044), Journal of Research of the National Bureau of Standards, 49(6), pp. 409–436, 1952.
  * A. Björck, T. Elfving and Z. Strakos, [*Stability of Conjugate Gradient and Lanczos Methods for Linear Least Squares Problems*](https://doi.org/10.1137/S089547989631202X), SIAM Journal on Matrix Analysis and Applications, 19(3), pp. 720–736, 1998.
