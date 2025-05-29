```
construct_jacobian_cache(
    prob, alg, f, fu, u = prob.u0, p = prob.p;
    autodiff = nothing, vjp_autodiff = nothing, jvp_autodiff = nothing,
    linsolve = missing
)
```

Construct a cache for the Jacobian of `f` w.r.t. `u`.

### Arguments

  * `prob`: A [`NonlinearProblem`](@ref) or a [`NonlinearLeastSquaresProblem`](@ref).
  * `alg`: A [`AbstractNonlinearSolveAlgorithm`](@ref). Used to check for [`concrete_jac`](@ref).
  * `f`: The function to compute the Jacobian of.
  * `fu`: The evaluation of `f(u, p)` or `f(_, u, p)`. Used to determine the size of the result cache and Jacobian.
  * `u`: The current value of the state.
  * `p`: The current value of the parameters.

### Keyword Arguments

  * `autodiff`: Automatic Differentiation or Finite Differencing backend for computing the jacobian. By default, selects a backend based on sparsity parameters, type of state, function properties, etc.
  * `vjp_autodiff`: Automatic Differentiation or Finite Differencing backend for computing the vector-Jacobian product.
  * `jvp_autodiff`: Automatic Differentiation or Finite Differencing backend for computing the Jacobian-vector product.
  * `linsolve`: Linear Solver Algorithm used to determine if we need a concrete jacobian or if possible we can just use a `JacobianOperator` instead.
