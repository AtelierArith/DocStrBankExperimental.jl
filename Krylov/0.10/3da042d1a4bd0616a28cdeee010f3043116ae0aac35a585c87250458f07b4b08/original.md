```
(x, stats) = bilq(A, b::AbstractVector{FC};
                  c::AbstractVector{FC}=b, transfer_to_bicg::Bool=true,
                  M=I, N=I, ldiv::Bool=false, atol::T=√eps(T),
                  rtol::T=√eps(T), itmax::Int=0, timemax::Float64=Inf,
                  verbose::Int=0, history::Bool=false,
                  callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(x, stats) = bilq(A, b, x0::AbstractVector; kwargs...)
```

BiLQ can be warm-started from an initial guess `x0` where `kwargs` are the same keyword arguments as above.

Solve the square linear system Ax = b of size n using BiLQ. BiLQ is based on the Lanczos biorthogonalization process and requires two initial vectors `b` and `c`. The relation `bᴴc ≠ 0` must be satisfied and by default `c = b`. When `A` is Hermitian and `b = c`, BiLQ is equivalent to SYMMLQ. BiLQ requires support for `adjoint(M)` and `adjoint(N)` if preconditioners are provided.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :bilq`.

For an in-place variant that reuses memory across solves, see [`bilq!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `n`;
  * `b`: a vector of length `n`.

#### Optional argument

  * `x0`: a vector of length `n` that represents an initial guess of the solution `x`.

#### Keyword arguments

  * `c`: the second initial vector of length `n` required by the Lanczos biorthogonalization process;
  * `transfer_to_bicg`: transfer from the BiLQ point to the BiCG point, when it exists. The transfer is based on the residual norm;
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

  * A. Montoison and D. Orban, [*BiLQ: An Iterative Method for Nonsymmetric Linear Systems with a Quasi-Minimum Error Property*](https://doi.org/10.1137/19M1290991), SIAM Journal on Matrix Analysis and Applications, 41(3), pp. 1145–1166, 2020.
  * R. Fletcher, [*Conjugate gradient methods for indefinite systems*](https://doi.org/10.1007/BFb0080116), Numerical Analysis, Springer, pp. 73–89, 1976.
