```
linsolve(A::AbstractMatrix, b::AbstractVector, [x₀, a₀::Number = 0, a₁::Number = 1]; kwargs...)
linsolve(f, b, [x₀, a₀::Number = 0, a₁::Number = 1]; kwargs...)
# expert version:
linsolve(f, b, x₀, algorithm, [a₀::Number = 0, a₁::Number = 1]; alg_rrule=algorithm)
```

Compute a solution `x` to the linear system `(a₀ + a₁ * A)*x = b` or `a₀ * x + a₁ * f(x) = b`, possibly using a starting guess `x₀`. Return the approximate solution `x` and a `ConvergenceInfo` structure.

### Arguments:

The linear map can be an `AbstractMatrix` (dense or sparse) or a general function or callable object. If no initial guess is specified, it is chosen as `(zero(a₀)*zero(a₁))*b` which should generate an object similar to `b` but initialized with zeros. The numbers `a₀` and `a₁` are optional arguments; they are applied implicitly, i.e. they do not contribute the computation time of applying the linear map or to the number of operations on vectors of type `x` and `b`.

### Return values:

The return value is always of the form `x, info = linsolve(...)` with

  * `x`: the approximate solution to the problem, similar type as the right hand side `b` but possibly with a different `scalartype`
  * `info`: an object of type [`ConvergenceInfo`], which has the following fields

      * `info.converged::Int`: takes value 0 or 1 depending on whether the solution was converged up to the requested tolerance
      * `info.residual`: residual `b - f(x)` of the approximate solution `x`
      * `info.normres::Real`: norm of the residual, i.e. `norm(info.residual)`
      * `info.numops::Int`: total number of times that the linear map was applied, i.e. the number of times that `f` was called, or a vector was multiplied with `A`
      * `info.numiter::Int`: number of times the Krylov subspace was restarted (see below)

!!! warning "Check for convergence"
    No warning is printed if no converged solution was found, so always check if `info.converged == 1`.


### Keyword arguments:

Keyword arguments are given by:

  * `verbosity::Int = 0`: verbosity level, i.e. 

      * 0 (suppress all messages)
      * 1 (only warnings)
      * 2 (information at the beginning and end)
      * 3 (progress info after every iteration)
  * `atol::Real`: the requested accuracy, i.e. absolute tolerance, on the norm of the residual.
  * `rtol::Real`: the requested accuracy on the norm of the residual, relative to the norm of the right hand side `b`.
  * `tol::Real`: the requested accuracy on the norm of the residual that is actually used by the algorithm; it defaults to `max(atol, rtol*norm(b))`. So either use `atol` and `rtol` or directly use `tol` (in which case the value of `atol` and `rtol` will be ignored).
  * `krylovdim::Integer`: the maximum dimension of the Krylov subspace that will be constructed.
  * `maxiter::Integer`: the number of times the Krylov subspace can be rebuilt; see below for further details on the algorithms.
  * `orth::Orthogonalizer`: the orthogonalization method to be used, see [`Orthogonalizer`](@ref)
  * `issymmetric::Bool`: if the linear map is symmetric, only meaningful if `T<:Real`
  * `ishermitian::Bool`: if the linear map is hermitian
  * `isposdef::Bool`: if the linear map is positive definite

The default values are given by `atol = KrylovDefaults.tol[]`, `rtol = KrylovDefaults.tol[]`, `tol = max(atol, rtol*norm(b))`, `krylovdim = KrylovDefaults.krylovdim[]`, `maxiter = KrylovDefaults.maxiter[]`, `orth = KrylovDefaults.orth`; see [`KrylovDefaults`](@ref) for details.

The default value for the last three parameters depends on the method. If an `AbstractMatrix` is used, `issymmetric`, `ishermitian` and `isposdef` are checked for that matrix, ortherwise the default values are `issymmetric = false`, `ishermitian = T <: Real && issymmetric` and `isposdef = false`.

The final keyword argument `alg_rrule` is relevant only when `linsolve` is used in a setting where reverse-mode automatic differentation will be used. A custom `ChainRulesCore.rrule` is defined for `linsolve`, which can be evaluated using different algorithms that can be specified via `alg_rrule`. As the pullback of `linsolve` involves solving a linear system with the (Hermitian) adjoint of the linear map, the default value is to use the same algorithm. This keyword argument should only be used when this default choice is failing or not performing efficiently. Check the documentation for more information on the possible values for `alg_rrule` and their implications on the algorithm being used.

### Algorithms

The final (expert) method, without default values and keyword arguments, is the one that is finally called, and can also be used directly. Here, one specifies the algorithm explicitly. Currently, only [`CG`](@ref), [`GMRES`](@ref), [`BiCGStab`](@ref) and [`LSMR`](@ref) are implemented, where `CG` is chosen if `isposdef == true` and `GMRES` is chosen otherwise. Note that in standard `GMRES` terminology, our parameter `krylovdim` is referred to as the *restart* parameter, and our `maxiter` parameter counts the number of outer iterations, i.e. restart cycles. In `CG`, the Krylov subspace is only implicit because short recurrence relations are being used, and therefore no restarts are required. Therefore, we pass `krylovdim*maxiter` as the maximal number of CG iterations that can be used by the `CG` algorithm.
