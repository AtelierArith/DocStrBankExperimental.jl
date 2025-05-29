```
(x, y, stats) = craig(A, b::AbstractVector{FC};
                      M=I, N=I, ldiv::Bool=false,
                      transfer_to_lsqr::Bool=false, sqd::Bool=false,
                      λ::T=zero(T), btol::T=√eps(T),
                      conlim::T=1/√eps(T), atol::T=√eps(T),
                      rtol::T=√eps(T), itmax::Int=0,
                      timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                      callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

Find the least-norm solution of the consistent linear system

```
Ax + λ²y = b
```

of size m × n using the Golub-Kahan implementation of Craig's method, where λ ≥ 0 is a regularization parameter. This method is equivalent to CGNE but is more stable.

For a system in the form Ax = b, Craig's method is equivalent to applying CG to AAᴴy = b and recovering x = Aᴴy. Note that y are the Lagrange multipliers of the least-norm problem

```
minimize ‖x‖  s.t.  Ax = b.
```

If `λ > 0`, CRAIG solves the symmetric and quasi-definite system

```
[ -F     Aᴴ ] [ x ]   [ 0 ]
[  A   λ²E  ] [ y ] = [ b ],
```

where E and F are symmetric and positive definite. Preconditioners M = E⁻¹ ≻ 0 and N = F⁻¹ ≻ 0 may be provided in the form of linear operators. If `sqd=true`, `λ` is set to the common value `1`.

The system above represents the optimality conditions of

```
min ‖x‖²_F + λ²‖y‖²_E  s.t.  Ax + λ²Ey = b.
```

For a symmetric and positive definite matrix `K`, the K-norm of a vector `x` is `‖x‖²_K = xᴴKx`. CRAIG is then equivalent to applying CG to `(AF⁻¹Aᴴ + λ²E)y = b` with `Fx = Aᴴy`.

If `λ = 0`, CRAIG solves the symmetric and indefinite system

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

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :craig`.

For an in-place variant that reuses memory across solves, see [`craig!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `m × n`;
  * `b`: a vector of length `m`.

#### Keyword arguments

  * `M`: linear operator that models a Hermitian positive-definite matrix of size `m` used for centered preconditioning of the augmented system;
  * `N`: linear operator that models a Hermitian positive-definite matrix of size `n` used for centered preconditioning of the augmented system;
  * `ldiv`: define whether the preconditioners use `ldiv!` or `mul!`;
  * `transfer_to_lsqr`: transfer from the LSLQ point to the LSQR point, when it exists. The transfer is based on the residual norm;
  * `sqd`: if `true`, set `λ=1` for Hermitian quasi-definite systems;
  * `λ`: regularization parameter;
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
  * `y`: a dense vector of length `m`;
  * `stats`: statistics collected on the run in a [`SimpleStats`](@ref) structure.

#### References

  * J. E. Craig, [*The N-step iteration procedures*](https://doi.org/10.1002/sapm195534164), Journal of Mathematics and Physics, 34(1-4), pp. 64–73, 1955.
  * C. C. Paige and M. A. Saunders, [*LSQR: An Algorithm for Sparse Linear Equations and Sparse Least Squares*](https://doi.org/10.1145/355984.355989), ACM Transactions on Mathematical Software, 8(1), pp. 43–71, 1982.
  * M. A. Saunders, [*Solutions of Sparse Rectangular Systems Using LSQR and CRAIG*](https://doi.org/10.1007/BF01739829), BIT Numerical Mathematics, 35(4), pp. 588–604, 1995.
