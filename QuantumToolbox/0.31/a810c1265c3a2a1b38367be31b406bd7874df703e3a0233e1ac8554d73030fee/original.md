```
sesolve(
    H::Union{AbstractQuantumObject{Operator},Tuple},
    ψ0::QuantumObject{Ket},
    tlist::AbstractVector;
    alg::OrdinaryDiffEqAlgorithm = Tsit5(),
    e_ops::Union{Nothing,AbstractVector,Tuple} = nothing,
    params = NullParameters(),
    progress_bar::Union{Val,Bool} = Val(true),
    inplace::Union{Val,Bool} = Val(true),
    kwargs...,
)
```

Time evolution of a closed quantum system using the Schrödinger equation:

$$
\frac{\partial}{\partial t} |\psi(t)\rangle = -i \hat{H} |\psi(t)\rangle
$$

# Arguments

  * `H`: Hamiltonian of the system $\hat{H}$. It can be either a [`QuantumObject`](@ref), a [`QuantumObjectEvolution`](@ref), or a `Tuple` of operator-function pairs.
  * `ψ0`: Initial state of the system $|\psi(0)\rangle$.
  * `tlist`: List of times at which to save either the state or the expectation values of the system.
  * `alg`: The algorithm for the ODE solver. The default is `Tsit5()`.
  * `e_ops`: List of operators for which to calculate expectation values. It can be either a `Vector` or a `Tuple`.
  * `params`: Parameters to pass to the solver. This argument is usually expressed as a `NamedTuple` or `AbstractVector` of parameters. For more advanced usage, any custom struct can be used.
  * `progress_bar`: Whether to show the progress bar. Using non-`Val` types might lead to type instabilities.
  * `inplace`: Whether to use the inplace version of the ODEProblem. The default is `Val(true)`. It is recommended to use `Val(true)` for better performance, but it is sometimes necessary to use `Val(false)`, for example when performing automatic differentiation using [Zygote.jl](https://github.com/FluxML/Zygote.jl).
  * `kwargs`: The keyword arguments for the ODEProblem.

# Notes

  * The states will be saved depend on the keyword argument `saveat` in `kwargs`.
  * If `e_ops` is empty, the default value of `saveat=tlist` (saving the states corresponding to `tlist`), otherwise, `saveat=[tlist[end]]` (only save the final state). You can also specify `e_ops` and `saveat` separately.
  * The default tolerances in `kwargs` are given as `reltol=1e-6` and `abstol=1e-8`.
  * For more details about `alg` please refer to [`DifferentialEquations.jl` (ODE Solvers)](https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/)
  * For more details about `kwargs` please refer to [`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)

# Returns

  * `sol::TimeEvolutionSol`: The solution of the time evolution. See also [`TimeEvolutionSol`](@ref)
