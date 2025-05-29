```
(x, stats) = lslq(A, b::AbstractVector{FC};
                  M=I, N=I, ldiv::Bool=false,
                  window::Int=5, transfer_to_lsqr::Bool=false,
                  sqd::Bool=false, λ::T=zero(T),
                  σ::T=zero(T), etol::T=√eps(T),
                  utol::T=√eps(T), btol::T=√eps(T),
                  conlim::T=1/√eps(T), atol::T=√eps(T),
                  rtol::T=√eps(T), itmax::Int=0,
                  timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                  callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

Solve the regularized linear least-squares problem

```
minimize ‖b - Ax‖₂² + λ²‖x‖₂²
```

of size m × n using the LSLQ method, where λ ≥ 0 is a regularization parameter. LSLQ is formally equivalent to applying SYMMLQ to the normal equations

```
(AᴴA + λ²I) x = Aᴴb
```

but is more stable.

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

For a symmetric and positive definite matrix `K`, the K-norm of a vector `x` is `‖x‖²_K = xᴴKx`. LSLQ is then equivalent to applying SYMMLQ to `(AᴴE⁻¹A + λ²F)x = AᴴE⁻¹b` with `r = E⁻¹(b - Ax)`.

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

#### Main features

  * the solution estimate is updated along orthogonal directions
  * the norm of the solution estimate ‖xᴸₖ‖₂ is increasing
  * the error ‖eₖ‖₂ := ‖xᴸₖ - x*‖₂ is decreasing
  * it is possible to transition cheaply from the LSLQ iterate to the LSQR iterate if there is an advantage (there always is in terms of error)
  * if `A` is rank deficient, identify the minimum least-squares solution

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :lslq`.

For an in-place variant that reuses memory across solves, see [`lslq!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `m × n`;
  * `b`: a vector of length `m`.

#### Keyword arguments

  * `M`: linear operator that models a Hermitian positive-definite matrix of size `m` used for centered preconditioning of the augmented system;
  * `N`: linear operator that models a Hermitian positive-definite matrix of size `n` used for centered preconditioning of the augmented system;
  * `ldiv`: define whether the preconditioners use `ldiv!` or `mul!`;
  * `window`: number of iterations used to accumulate a lower bound on the error;
  * `transfer_to_lsqr`: transfer from the LSLQ point to the LSQR point, when it exists. The transfer is based on the residual norm;
  * `sqd`: if `true`, set `λ=1` for Hermitian quasi-definite systems;
  * `λ`: regularization parameter;
  * `σ`: strict lower bound on the smallest positive singular value `σₘᵢₙ` such as `σ = (1-10⁻⁷)σₘᵢₙ`;
  * `etol`: stopping tolerance based on the lower bound on the error;
  * `utol`: stopping tolerance based on the upper bound on the error;
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
  * `stats`: statistics collected on the run in a [`LSLQStats`](@ref) structure.
  * `stats.err_lbnds` is a vector of lower bounds on the LQ error–-the vector is empty if `window` is set to zero
  * `stats.err_ubnds_lq` is a vector of upper bounds on the LQ error–-the vector is empty if `σ == 0` is left at zero
  * `stats.err_ubnds_cg` is a vector of upper bounds on the CG error–-the vector is empty if `σ == 0` is left at zero
  * `stats.error_with_bnd` is a boolean indicating whether there was an error in the upper bounds computation (cancellation errors, too large σ ...)

#### Stopping conditions

The iterations stop as soon as one of the following conditions holds true:

  * the optimality residual is sufficiently small (`stats.status = "found approximate minimum least-squares solution"`) in the sense that either

      * ‖Aᴴr‖ / (‖A‖ ‖r‖) ≤ atol, or
      * 1 + ‖Aᴴr‖ / (‖A‖ ‖r‖) ≤ 1
  * an approximate zero-residual solution has been found (`stats.status = "found approximate zero-residual solution"`) in the sense that either

      * ‖r‖ / ‖b‖ ≤ btol + atol ‖A‖ * ‖xᴸ‖ / ‖b‖, or
      * 1 + ‖r‖ / ‖b‖ ≤ 1
  * the estimated condition number of `A` is too large in the sense that either

      * 1/cond(A) ≤ 1/conlim (`stats.status = "condition number exceeds tolerance"`), or
      * 1 + 1/cond(A) ≤ 1 (`stats.status = "condition number seems too large for this machine"`)
  * the lower bound on the LQ forward error is less than etol * ‖xᴸ‖
  * the upper bound on the CG forward error is less than utol * ‖xᶜ‖

#### References

  * R. Estrin, D. Orban and M. A. Saunders, [*Euclidean-norm error bounds for SYMMLQ and CG*](https://doi.org/10.1137/16M1094816), SIAM Journal on Matrix Analysis and Applications, 40(1), pp. 235–253, 2019.
  * R. Estrin, D. Orban and M. A. Saunders, [*LSLQ: An Iterative Method for Linear Least-Squares with an Error Minimization Property*](https://doi.org/10.1137/17M1113552), SIAM Journal on Matrix Analysis and Applications, 40(1), pp. 254–275, 2019.
