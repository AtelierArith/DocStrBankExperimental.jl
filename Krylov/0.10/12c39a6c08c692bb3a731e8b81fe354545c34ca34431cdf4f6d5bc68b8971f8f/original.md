```
(x, stats) = cg_lanczos_shift(A, b::AbstractVector{FC}, shifts::AbstractVector{T};
                              M=I, ldiv::Bool=false,
                              check_curvature::Bool=false, atol::T=√eps(T),
                              rtol::T=√eps(T), itmax::Int=0,
                              timemax::Float64=Inf, verbose::Int=0,
                              history::Bool=false, callback=workspace->false,
                              iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

The Lanczos version of the conjugate gradient method to solve a family of shifted systems

```
(A + αI) x = b  (α = α₁, ..., αₚ)
```

of size n. The method does *not* abort if A + αI is not definite.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :cg_lanczos_shift`.

For an in-place variant that reuses memory across solves, see [`cg_lanczos_shift!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a Hermitian matrix of dimension `n`;
  * `b`: a vector of length `n`;
  * `shifts`: a vector of length `p`.

#### Keyword arguments

  * `M`: linear operator that models a Hermitian positive-definite matrix of size `n` used for centered preconditioning;
  * `ldiv`: define whether the preconditioner uses `ldiv!` or `mul!`;
  * `check_curvature`: if `true`, check that the curvature of the quadratic along the search direction is positive, and abort if not;
  * `atol`: absolute stopping tolerance based on the residual norm;
  * `rtol`: relative stopping tolerance based on the residual norm;
  * `itmax`: the maximum number of iterations. If `itmax=0`, the default number of iterations is set to `2n`;
  * `timemax`: the time limit in seconds;
  * `verbose`: additional details can be displayed if verbose mode is enabled (verbose > 0). Information will be displayed every `verbose` iterations;
  * `history`: collect additional statistics on the run such as residual norms, or Aᴴ-residual norms;
  * `callback`: function or functor called as `callback(workspace)` that returns `true` if the Krylov method should terminate, and `false` otherwise;
  * `iostream`: stream to which output is logged.

#### Output arguments

  * `x`: a vector of `p` dense vectors, each one of length `n`;
  * `stats`: statistics collected on the run in a [`LanczosShiftStats`](@ref) structure.

#### References

  * A. Frommer and P. Maass, [*Fast CG-Based Methods for Tikhonov-Phillips Regularization*](https://doi.org/10.1137/S1064827596313310), SIAM Journal on Scientific Computing, 20(5), pp. 1831–1850, 1999.
  * C. C. Paige and M. A. Saunders, [*Solution of Sparse Indefinite Systems of Linear Equations*](https://doi.org/10.1137/0712047), SIAM Journal on Numerical Analysis, 12(4), pp. 617–629, 1975.
