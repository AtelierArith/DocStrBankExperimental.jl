```
(x, stats) = cgs(A, b::AbstractVector{FC};
                 c::AbstractVector{FC}=b, M=I, N=I,
                 ldiv::Bool=false, atol::T=√eps(T),
                 rtol::T=√eps(T), itmax::Int=0,
                 timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                 callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(x, stats) = cgs(A, b, x0::AbstractVector; kwargs...)
```

CGS can be warm-started from an initial guess `x0` where `kwargs` are the same keyword arguments as above.

Solve the consistent linear system Ax = b of size n using CGS. CGS requires two initial vectors `b` and `c`. The relation `bᴴc ≠ 0` must be satisfied and by default `c = b`.

From "Iterative Methods for Sparse Linear Systems (Y. Saad)" :

«The method is based on a polynomial variant of the conjugate gradients algorithm. Although related to the so-called bi-conjugate gradients (BCG) algorithm, it does not involve adjoint matrix-vector multiplications, and the expected convergence rate is about twice that of the BCG algorithm.

The Conjugate Gradient Squared algorithm works quite well in many cases. However, one difficulty is that, since the polynomials are squared, rounding errors tend to be more damaging than in the standard BCG algorithm. In particular, very high variations of the residual vectors often cause the residual norms computed to become inaccurate.

TFQMR and BICGSTAB were developed to remedy this difficulty.»

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :cgs`.

For an in-place variant that reuses memory across solves, see [`cgs!`](@ref).

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

#### Reference

  * P. Sonneveld, [*CGS, A Fast Lanczos-Type Solver for Nonsymmetric Linear systems*](https://doi.org/10.1137/0910004), SIAM Journal on Scientific and Statistical Computing, 10(1), pp. 36–52, 1989.
