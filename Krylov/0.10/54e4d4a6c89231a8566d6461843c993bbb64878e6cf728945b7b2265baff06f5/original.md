```
(x, stats) = bicgstab(A, b::AbstractVector{FC};
                      c::AbstractVector{FC}=b, M=I, N=I,
                      ldiv::Bool=false, atol::T=√eps(T),
                      rtol::T=√eps(T), itmax::Int=0,
                      timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                      callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(x, stats) = bicgstab(A, b, x0::AbstractVector; kwargs...)
```

BICGSTAB can be warm-started from an initial guess `x0` where `kwargs` are the same keyword arguments as above.

Solve the square linear system Ax = b of size n using BICGSTAB. BICGSTAB requires two initial vectors `b` and `c`. The relation `bᴴc ≠ 0` must be satisfied and by default `c = b`.

The Biconjugate Gradient Stabilized method is a variant of BiCG, like CGS, but using different updates for the Aᴴ-sequence in order to obtain smoother convergence than CGS.

If BICGSTAB stagnates, we recommend DQGMRES and BiLQ as alternative methods for unsymmetric square systems.

BICGSTAB stops when `itmax` iterations are reached or when `‖rₖ‖ ≤ atol + ‖b‖ * rtol`.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :bicgstab`.

For an in-place variant that reuses memory across solves, see [`bicgstab!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `n`;
  * `b`: a vector of length `n`.

#### Optional argument

  * `x0`: a vector of length `n` that represents an initial guess of the solution `x`.

#### Keyword arguments

  * `c`: the second initial vector of length `n` required by the Lanczos biorthogonalization process;
  * `M`: linear operator that models a nonsingular matrix of size `n` used for left preconditioning;
  * `N`: linear operator that models a nonsingular matrix of size `n` used for right preconditioning;
  * `ldiv`: define whether the preconditioners use `ldiv!` or `mul!`;
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

#### References

  * H. A. van der Vorst, [*Bi-CGSTAB: A fast and smoothly converging variant of Bi-CG for the solution of nonsymmetric linear systems*](https://doi.org/10.1137/0913035), SIAM Journal on Scientific and Statistical Computing, 13(2), pp. 631–644, 1992.
  * G. L.G. Sleijpen and D. R. Fokkema, [*BiCGstab(ℓ) for linear equations involving unsymmetric matrices with complex spectrum*](https://etna.math.kent.edu/volumes/1993-2000/vol1/abstract.php?vol=1&pages=11-32), Electronic Transactions on Numerical Analysis, 1, pp. 11–32, 1993.
