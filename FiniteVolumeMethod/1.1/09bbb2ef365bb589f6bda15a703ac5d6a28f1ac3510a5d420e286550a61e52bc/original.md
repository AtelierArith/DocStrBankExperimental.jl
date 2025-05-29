```
solve(prob::SteadyFVMProblem, alg; 
    specialization=SciMLBase.AutoSpecialize, 
    jac_prototype=jacobian_sparsity(prob),
    parallel::Val{<:Bool}=Val(true),
    kwargs...)
```

Solves the given [`FVMProblem`](@ref) or [`FVMSystem`](@ref) `prob` with the algorithm `alg`.

# Arguments

  * `prob`: The problem to be solved.
  * `alg`: The algorithm to be used to solve the problem. This can be any of the algorithms in NonlinearSolve.jl.

# Keyword Arguments

  * `specialization=SciMLBase.AutoSpecialize`: The type of specialization to be used. See https://docs.sciml.ai/DiffEqDocs/stable/features/low_dep/#Controlling-Function-Specialization-and-Precompilation.
  * `jac_prototype=jacobian_sparsity(prob)`: The prototype for the Jacobian matrix, constructed by default from `jacobian_sparsity`.
  * `parallel::Val{<:Bool}=Val(true)`: Whether to use multithreading. Use `Val(false)` to disable multithreading.
  * `kwargs...`: Any other keyword arguments to be passed to the solver.

# Outputs

The returned value `sol` depends on whether the underlying problem is a [`FVMProblem`](@ref) or an [`FVMSystem`](@ref), but in  each case it is an `ODESolution` type that can be accessed like the solutions in DifferentialEquations.jl:

  * [`FVMProblem`](@ref)

In this case, `sol` is such that the `i`th component of `sol` refers to the `i`th node of the underlying mesh.

  * [`FVMSystem`](@ref)

In this case, the `(j, i)`th component of `sol` refers to the `i`th node of the underlying mesh for the `j`th component of the system.
