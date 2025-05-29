```
augnewton([eltype], nep::NEP; [errmeasure,][tol,][maxit,][λ,][v,][c,][logger,][linsolvercreator,][armijo_factor,][armijo_max])
```

Run the augmented Newton method. The method is equivalent to `newton()` in exact arithmetic,  but works only with operations on vectors of length `n`.

The following keyword arguments are in common for many NEP-solvers:

  * `logger` is either a [`Logger`](@ref) object or an `Int`. If it is an `Int`, a `PrintLogger(logger)` will be instantiated. `logger=0` prints nothing, `logger=1` prints more, etc.
  * `errmeasure` determines how error is measured. It is either a function handle or an object of the type `Errmeasure`.  If it is a function handle, it should take `(λ,v)` as input and return a real scalar (the error). See [`Errmeasure`](@ref) and [`ErrmeasureType`](@ref) for further description.
  * `tol` is a scalar which determines termination. If `errmeasure` is less than `tol` the eigenpair is marked as converged.
  * The scalar `λ` and the vector `v` are starting approximations.
  * `maxit` determines the maximum number of iterations. The error `NoConvergenceException` is thrown if this is exceeded.
  * The `linsolvecreator` specifies how the linear system should be solved. See [`LinSolver`](@ref) for further information.
  * `armijo_factor` specifies if an Armijo rule should be applied, and its value specifies the scaling factor of the step length (per reduction step). The variable `armijo_max` specifies the maximum number of step length reductions.

# Example

This illustrates the equivalence between `newton` and `augnewton`.

```julia-repl
julia> nep=nep_gallery("dep1")
julia> λ1,v1=newton(nep,maxit=20,v=ones(size(nep,1)),λ=0)
julia> λ2,v2=augnewton(nep,maxit=20,v=ones(size(nep,1)),λ=0)
julia> λ1-λ2
0.0 + 0.0im
```

# References

  * Nichtlineare Behandlung von Eigenwertaufgaben, Z. Angew. Math. Mech. 30 (1950) 281-282.
  * A. Ruhe, Algorithms for the nonlinear eigenvalue problem, SIAM J. Numer. Anal. 10 (1973) 674-689
