```
(x, y, stats) = bilqr(A, b::AbstractVector{FC}, c::AbstractVector{FC};
                      transfer_to_bicg::Bool=true, atol::T=√eps(T),
                      rtol::T=√eps(T), itmax::Int=0,
                      timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                      callback=workspace->false, iostream::IO=kstdout)
```

`T` is an `AbstractFloat` such as `Float32`, `Float64` or `BigFloat`. `FC` is `T` or `Complex{T}`.

```
(x, y, stats) = bilqr(A, b, c, x0::AbstractVector, y0::AbstractVector; kwargs...)
```

BiLQR can be warm-started from initial guesses `x0` and `y0` where `kwargs` are the same keyword arguments as above.

Combine BiLQ and QMR to solve adjoint systems.

```
[0  A] [y] = [b]
[Aᴴ 0] [x]   [c]
```

The relation `bᴴc ≠ 0` must be satisfied. BiLQ is used for solving primal system `Ax = b` of size n. QMR is used for solving dual system `Aᴴy = c` of size n.

#### Interface

To easily switch between Krylov methods, use the generic interface [`krylov_solve`](@ref) with `method = :bilqr`.

For an in-place variant that reuses memory across solves, see [`bilqr!`](@ref).

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `n`;
  * `b`: a vector of length `n`;
  * `c`: a vector of length `n`.

#### Optional arguments

  * `x0`: a vector of length `n` that represents an initial guess of the solution `x`;
  * `y0`: a vector of length `n` that represents an initial guess of the solution `y`.

#### Keyword arguments

  * `transfer_to_bicg`: transfer from the BiLQ point to the BiCG point, when it exists. The transfer is based on the residual norm;
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
  * `y`: a dense vector of length `n`;
  * `stats`: statistics collected on the run in an [`AdjointStats`](@ref) structure.

#### Reference

  * A. Montoison and D. Orban, [*BiLQ: An Iterative Method for Nonsymmetric Linear Systems with a Quasi-Minimum Error Property*](https://doi.org/10.1137/19M1290991), SIAM Journal on Matrix Analysis and Applications, 41(3), pp. 1145–1166, 2020.
