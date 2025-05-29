```
(x, y, stats) = craigmr(A, b::AbstractVector{FC};
                        M=I, N=I, ldiv::Bool=false,
                        sqd::Bool=false, λ::T=zero(T), atol::T=√eps(T),
                        rtol::T=√eps(T), itmax::Int=0,
                        timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                        callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

Solve the consistent linear system

```
Ax + λ²y = b
```

of size m × n using the CRAIGMR method, where λ ≥ 0 is a regularization parameter. This method is equivalent to applying the Conjugate Residuals method to the normal equations of the second kind

```
(AAᴴ + λ²I) y = b
```

but is more stable. When λ = 0, this method solves the minimum-norm problem

```
min ‖x‖  s.t.  x ∈ argmin ‖Ax - b‖.
```

If `λ > 0`, CRAIGMR solves the symmetric and quasi-definite system

```
[ -F    Aᴴ ] [ x ]   [ 0 ]
[  A  λ²E  ] [ y ] = [ b ],
```

where E and F are symmetric and positive definite. Preconditioners M = E⁻¹ ≻ 0 and N = F⁻¹ ≻ 0 may be provided in the form of linear operators. If `sqd=true`, `λ` is set to the common value `1`.

The system above represents the optimality conditions of

```
min ‖x‖²_F + λ²‖y‖²_E  s.t.  Ax + λ²Ey = b.
```

For a symmetric and positive definite matrix `K`, the K-norm of a vector `x` is `‖x‖²_K = xᴴKx`. CRAIGMR is then equivalent to applying MINRES to `(AF⁻¹Aᴴ + λ²E)y = b` with `Fx = Aᴴy`.

If `λ = 0`, CRAIGMR solves the symmetric and indefinite system

```
[ -F   Aᴴ ] [ x ]   [ 0 ]
[  A   0  ] [ y ] = [ b ].
```

The system above represents the optimality conditions of

```
min ‖x‖²_F  s.t.  Ax = b.
```

In this case, `M` can still be specified and indicates the weighted norm in which residuals are measured.

CRAIGMR produces monotonic residuals ‖r‖₂. It is formally equivalent to CRMR, though can be slightly more accurate, and intricate to implement. Both the x- and y-parts of the solution are returned.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :craigmr`.

For an in-place variant that reuses memory across solves, see [`craigmr!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `m × n`;
  * `b`: a vector of length `m`.

#### Keyword arguments

  * `M`: linear operator that models a Hermitian positive-definite matrix of size `m` used for centered preconditioning of the augmented system;
  * `N`: linear operator that models a Hermitian positive-definite matrix of size `n` used for centered preconditioning of the augmented system;
  * `ldiv`: define whether the preconditioners use `ldiv!` or `mul!`;
  * `sqd`: if `true`, set `λ=1` for Hermitian quasi-definite systems;
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
  * `y`: a dense vector of length `m`;
  * `stats`: statistics collected on the run in a [`SimpleStats`](@ref) structure.

#### References

  * D. Orban and M. Arioli. [*Iterative Solution of Symmetric Quasi-Definite Linear Systems*](https://doi.org/10.1137/1.9781611974737), Volume 3 of Spotlights. SIAM, Philadelphia, PA, 2017.
  * D. Orban, [*The Projected Golub-Kahan Process for Constrained, Linear Least-Squares Problems*](https://dx.doi.org/10.13140/RG.2.2.17443.99360). Cahier du GERAD G-2014-15, 2014.
