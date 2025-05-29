```
(x, stats) = minres_qlp(A, b::AbstractVector{FC};
                        M=I, ldiv::Bool=false, Artol::T=√eps(T),
                        λ::T=zero(T), atol::T=√eps(T),
                        rtol::T=√eps(T), itmax::Int=0,
                        timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                        callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(x, stats) = minres_qlp(A, b, x0::AbstractVector; kwargs...)
```

MINRES-QLP can be warm-started from an initial guess `x0` where `kwargs` are the same keyword arguments as above.

MINRES-QLP is the only method based on the Lanczos process that returns the minimum-norm solution on singular inconsistent systems (A + λI)x = b of size n, where λ is a shift parameter. It is significantly more complex but can be more reliable than MINRES when A is ill-conditioned.

M also indicates the weighted norm in which residuals are measured.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :minres_qlp`.

For an in-place variant that reuses memory across solves, see [`minres_qlp!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a Hermitian matrix of dimension `n`;
  * `b`: a vector of length `n`.

#### Optional argument

  * `x0`: a vector of length `n` that represents an initial guess of the solution `x`.

#### Keyword arguments

  * `M`: linear operator that models a Hermitian positive-definite matrix of size `n` used for centered preconditioning;
  * `ldiv`: define whether the preconditioner uses `ldiv!` or `mul!`;
  * `λ`: regularization parameter;
  * `atol`: absolute stopping tolerance based on the residual norm;
  * `rtol`: relative stopping tolerance based on the residual norm;
  * `Artol`: relative stopping tolerance based on the Aᴴ-residual norm;
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

  * S.-C. T. Choi, *Iterative methods for singular linear equations and least-squares problems*, Ph.D. thesis, ICME, Stanford University, 2006.
  * S.-C. T. Choi, C. C. Paige and M. A. Saunders, [*MINRES-QLP: A Krylov subspace method for indefinite or singular symmetric systems*](https://doi.org/10.1137/100787921), SIAM Journal on Scientific Computing, Vol. 33(4), pp. 1810–1836, 2011.
  * S.-C. T. Choi and M. A. Saunders, [*Algorithm 937: MINRES-QLP for symmetric and Hermitian linear equations and least-squares problems*](https://doi.org/10.1145/2527267), ACM Transactions on Mathematical Software, 40(2), pp. 1–12, 2014.
