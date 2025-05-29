```
(x, y, stats) = lnlq(A, b::AbstractVector{FC};
                     M=I, N=I, ldiv::Bool=false,
                     transfer_to_craig::Bool=true,
                     sqd::Bool=false, λ::T=zero(T),
                     σ::T=zero(T), utolx::T=√eps(T),
                     utoly::T=√eps(T), atol::T=√eps(T),
                     rtol::T=√eps(T), itmax::Int=0,
                     timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                     callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

Find the least-norm solution of the consistent linear system

```
Ax + λ²y = b
```

of size m × n using the LNLQ method, where λ ≥ 0 is a regularization parameter.

For a system in the form Ax = b, LNLQ method is equivalent to applying SYMMLQ to AAᴴy = b and recovering x = Aᴴy but is more stable. Note that y are the Lagrange multipliers of the least-norm problem

```
minimize ‖x‖  s.t.  Ax = b.
```

If `λ > 0`, LNLQ solves the symmetric and quasi-definite system

```
[ -F    Aᴴ ] [ x ]   [ 0 ]
[  A  λ²E  ] [ y ] = [ b ],
```

where E and F are symmetric and positive definite. Preconditioners M = E⁻¹ ≻ 0 and N = F⁻¹ ≻ 0 may be provided in the form of linear operators. If `sqd=true`, `λ` is set to the common value `1`.

The system above represents the optimality conditions of

```
min ‖x‖²_F + λ²‖y‖²_E  s.t.  Ax + λ²Ey = b.
```

For a symmetric and positive definite matrix `K`, the K-norm of a vector `x` is `‖x‖²_K = xᴴKx`. LNLQ is then equivalent to applying SYMMLQ to `(AF⁻¹Aᴴ + λ²E)y = b` with `Fx = Aᴴy`.

If `λ = 0`, LNLQ solves the symmetric and indefinite system

```
[ -F   Aᴴ ] [ x ]   [ 0 ]
[  A   0  ] [ y ] = [ b ].
```

The system above represents the optimality conditions of

```
minimize ‖x‖²_F  s.t.  Ax = b.
```

In this case, `M` can still be specified and indicates the weighted norm in which residuals are measured.

In this implementation, both the x and y-parts of the solution are returned.

`utolx` and `utoly` are tolerances on the upper bound of the distance to the solution ‖x-x*‖ and ‖y-y*‖, respectively. The bound is valid if λ>0 or σ>0 where σ should be strictly smaller than the smallest positive singular value. For instance σ:=(1-1e-7)σₘᵢₙ .

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :lnlq`.

For an in-place variant that reuses memory across solves, see [`lnlq!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `m × n`;
  * `b`: a vector of length `m`.

#### Keyword arguments

  * `M`: linear operator that models a Hermitian positive-definite matrix of size `m` used for centered preconditioning of the augmented system;
  * `N`: linear operator that models a Hermitian positive-definite matrix of size `n` used for centered preconditioning of the augmented system;
  * `ldiv`: define whether the preconditioners use `ldiv!` or `mul!`;
  * `transfer_to_craig`: transfer from the LNLQ point to the CRAIG point, when it exists. The transfer is based on the residual norm;
  * `sqd`: if `true`, set `λ=1` for Hermitian quasi-definite systems;
  * `λ`: regularization parameter;
  * `σ`: strict lower bound on the smallest positive singular value `σₘᵢₙ` such as `σ = (1-10⁻⁷)σₘᵢₙ`;
  * `utolx`: tolerance on the upper bound on the distance to the solution `‖x-x*‖`;
  * `utoly`: tolerance on the upper bound on the distance to the solution `‖y-y*‖`;
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
  * `y`: a dense vector of length `m`;
  * `stats`: statistics collected on the run in a [`LNLQStats`](@ref) structure.

#### Reference

  * R. Estrin, D. Orban, M.A. Saunders, [*LNLQ: An Iterative Method for Least-Norm Problems with an Error Minimization Property*](https://doi.org/10.1137/18M1194948), SIAM Journal on Matrix Analysis and Applications, 40(3), pp. 1102–1124, 2019.
