```
reallinsolve(f, b, x₀, algorithm, [a₀::Real = 0, a₁::Real = 1]; alg_rrule=algorithm)
```

Compute a solution `x` to the linear system `a₀ * x + a₁ * f(x) = b`, using a starting guess `x₀`, where `f` represents a real linear map. Return the approximate solution `x` and a `ConvergenceInfo` structure.

!!! note "Note about real linear maps"
    A function `f` is said to implement a real linear map if it satisfies  `f(add(x,y)) = add(f(x), f(y)` and `f(scale(x, α)) = scale(f(x), α)` for vectors `x` and `y` and scalars `α::Real`. Note that this is possible even when the vectors are represented using complex arithmetic. For example, the map `f=x-> x + conj(x)` represents a real linear map that is not (complex) linear, as it does not satisfy `f(scale(x, α)) = scale(f(x), α)` for complex scalars `α`. Note that complex linear maps are always real linear maps and thus can be used in this context, though in that case `linsolve` and `reallinsolve` target the same solution. However, they still compute that solution using different arithmetic, and in that case `linsolve` might be more efficient.

    To interpret the vectors `x` and `y` as elements from a real vector space, the standard inner product defined on them will be replaced with `real(inner(x,y))`. This has no effect if the vectors `x` and `y` were represented using real arithmetic to begin with, and allows to seemlessly use complex vectors as well.


### Arguments:

The linear map can be an `AbstractMatrix` (dense or sparse) or a general function or callable object. The real numbers `a₀` and `a₁` are optional arguments; they are applied  implicitly,  i.e. they do not contribute the computation time of applying the linear map or to the  number of operations on vectors of type `x` and `b`.

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


### Algorithms

The final (expert) method, without default values and keyword arguments, is the one that is finally called, and can also be used directly. Here, one specifies the algorithm explicitly. Currently, only [`CG`](@ref), [`GMRES`](@ref) and [`BiCGStab`](@ref) are implemented, where `CG` is chosen if `isposdef == true` and `GMRES` is chosen otherwise. Note that in standard `GMRES` terminology, our parameter `krylovdim` is referred to as the *restart* parameter, and our `maxiter` parameter counts the number of outer iterations, i.e. restart cycles. In `CG`, the Krylov subspace is only implicit because short recurrence relations are being used, and therefore no restarts are required. Therefore, we pass `krylovdim*maxiter` as the maximal number of CG iterations that can be used by the `CG` algorithm.
