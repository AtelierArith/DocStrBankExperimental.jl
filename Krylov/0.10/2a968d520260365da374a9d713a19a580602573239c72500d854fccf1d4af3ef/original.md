```
(x, stats) = lsmr(A, b::AbstractVector{FC};
                  M=I, N=I, ldiv::Bool=false,
                  window::Int=5, sqd::Bool=false, λ::T=zero(T),
                  radius::T=zero(T), etol::T=√eps(T),
                  axtol::T=√eps(T), btol::T=√eps(T),
                  conlim::T=1/√eps(T), atol::T=zero(T),
                  rtol::T=zero(T), itmax::Int=0,
                  timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                  callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

Solve the regularized linear least-squares problem

```
minimize ‖b - Ax‖₂² + λ²‖x‖₂²
```

of size m × n using the LSMR method, where λ ≥ 0 is a regularization parameter. LSMR is formally equivalent to applying MINRES to the normal equations

```
(AᴴA + λ²I) x = Aᴴb
```

(and therefore to CRLS) but is more stable.

LSMR produces monotonic residuals ‖r‖₂ and optimality residuals ‖Aᴴr‖₂. It is formally equivalent to CRLS, though can be substantially more accurate.

LSMR can be also used to find a null vector of a singular matrix A by solving the problem `min ‖Aᴴx - b‖` with any nonzero vector `b`. At a minimizer, the residual vector `r = b - Aᴴx` will satisfy `Ar = 0`.

If `λ > 0`, we solve the symmetric and quasi-definite system

```
[ E      A ] [ r ]   [ b ]
[ Aᴴ  -λ²F ] [ x ] = [ 0 ],
```

where E and F are symmetric and positive definite. Preconditioners M = E⁻¹ ≻ 0 and N = F⁻¹ ≻ 0 may be provided in the form of linear operators. If `sqd=true`, `λ` is set to the common value `1`.

The system above represents the optimality conditions of

```
minimize ‖b - Ax‖²_E⁻¹ + λ²‖x‖²_F.
```

For a symmetric and positive definite matrix `K`, the K-norm of a vector `x` is `‖x‖²_K = xᴴKx`. LSMR is then equivalent to applying MINRES to `(AᴴE⁻¹A + λ²F)x = AᴴE⁻¹b` with `r = E⁻¹(b - Ax)`.

If `λ = 0`, we solve the symmetric and indefinite system

```
[ E    A ] [ r ]   [ b ]
[ Aᴴ   0 ] [ x ] = [ 0 ].
```

The system above represents the optimality conditions of

```
minimize ‖b - Ax‖²_E⁻¹.
```

In this case, `N` can still be specified and indicates the weighted norm in which `x` and `Aᴴr` should be measured. `r` can be recovered by computing `E⁻¹(b - Ax)`.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :lsmr`.

For an in-place variant that reuses memory across solves, see [`lsmr!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `m × n`;
  * `b`: a vector of length `m`.

#### Keyword arguments

  * `M`: linear operator that models a Hermitian positive-definite matrix of size `m` used for centered preconditioning of the augmented system;
  * `N`: linear operator that models a Hermitian positive-definite matrix of size `n` used for centered preconditioning of the augmented system;
  * `ldiv`: define whether the preconditioners use `ldiv!` or `mul!`;
  * `window`: number of iterations used to accumulate a lower bound on the error;
  * `sqd`: if `true`, set `λ=1` for Hermitian quasi-definite systems;
  * `λ`: regularization parameter;
  * `radius`: add the trust-region constraint ‖x‖ ≤ `radius` if `radius > 0`. Useful to compute a step in a trust-region method for optimization;
  * `etol`: stopping tolerance based on the lower bound on the error;
  * `axtol`: tolerance on the backward error;
  * `btol`: stopping tolerance used to detect zero-residual problems;
  * `conlim`: limit on the estimated condition number of `A` beyond which the solution will be abandoned;
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
  * `stats`: statistics collected on the run in a [`LsmrStats`](@ref) structure.

#### Reference

  * D. C.-L. Fong and M. A. Saunders, [*LSMR: An Iterative Algorithm for Sparse Least Squares Problems*](https://doi.org/10.1137/10079687X), SIAM Journal on Scientific Computing, 33(5), pp. 2950–2971, 2011.
