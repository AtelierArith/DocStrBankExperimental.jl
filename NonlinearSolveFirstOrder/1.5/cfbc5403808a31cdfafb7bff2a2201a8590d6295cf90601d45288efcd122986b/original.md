```
RobustMultiNewton(
    ::Type{T} = Float64;
    concrete_jac = nothing,
    linsolve = nothing,
    autodiff = nothing, vjp_autodiff = nothing, jvp_autodiff = nothing
)
```

A polyalgorithm focused on robustness. It uses a mixture of Newton methods with different globalizing techniques (trust region updates, line searches, etc.) in order to find a method that is able to adequately solve the minimization problem.

Basically, if this algorithm fails, then "most" good ways of solving your problem fail and you may need to think about reformulating the model (either there is an issue with the model, or more precision / more stable linear solver choice is required).

### Arguments

  * `T`: The eltype of the initial guess. It is only used to check if some of the algorithms are compatible with the problem type. Defaults to `Float64`.
