```
FVMSystem(prob1, prob2, ..., probN)
```

Constructs a representation for a system of PDEs, where each `probi` is  a [`FVMProblem`](@ref) for the `i`th component of the system.

For these [`FVMProblem`](@ref)s, the functions involved, such as the condition functions, should  all be defined so that the `u` argument assumes the form `u = (u₁, u₂, ..., uN)` (both `Tuple`s and `Vector`s will be passed),  where `uᵢ` is the solution for the `i`th component of the system. For the flux functions,  which for a [`FVMProblem`](@ref) takes the form

```
q(x, y, t, α, β, γ, p) ↦ (qx, qy),
```

the same form is used, except `α`, `β`, `γ` are all `Tuple`s so that `α[i]*x + β[i]*y + γ[i]` is the  approximation to `uᵢ`. 

!!! warning "Providing default flux functions"
    Due to this difference in flux functions, and the need to provide  `α`, `β`, and `γ` to the flux function, for `FVMSystem`s you need to  provide a flux function rather than a diffusion function. If you do provide a diffusion function, it will error when you try to solve  the problem.


This problem is solved in the same way as a [`FVMProblem`](@ref), except the problem is defined such that  the solution returns a matrix at each time, where the `(j, i)`th component corresponds to the solution at the `i`th  node for the `j`th component.

See also [`FVMProblem`](@ref) and [`SteadyFVMProblem`](@ref).

!!! note
    To construct a steady-state problem for an `FVMSystem`, you need to apply  [`SteadyFVMProblem`](@ref) to the system rather than first applying it to each individual [`FVMProblem`](@ref) in the system.

