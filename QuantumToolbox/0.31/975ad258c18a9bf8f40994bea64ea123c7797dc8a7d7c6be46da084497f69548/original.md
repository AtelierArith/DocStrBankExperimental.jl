```
smesolveProblem(
    H::Union{AbstractQuantumObject{Operator},Tuple},
    ψ0::QuantumObject,
    tlist::AbstractVector,
    c_ops::Union{Nothing,AbstractVector,Tuple} = nothing,
    sc_ops::Union{Nothing,AbstractVector,Tuple,AbstractQuantumObject} = nothing;
    e_ops::Union{Nothing,AbstractVector,Tuple} = nothing,
    params = NullParameters(),
    rng::AbstractRNG = default_rng(),
    progress_bar::Union{Val,Bool} = Val(true),
    store_measurement::Union{Val, Bool} = Val(false),
    kwargs...,
)
```

Generate the SDEProblem for the Stochastic Master Equation time evolution of an open quantum system. This is defined by the following stochastic differential equation:

$$
d \rho (t) = -i [\hat{H}, \rho(t)] dt + \sum_i \mathcal{D}[\hat{C}_i] \rho(t) dt + \sum_n \mathcal{D}[\hat{S}_n] \rho(t) dt + \sum_n \mathcal{H}[\hat{S}_n] \rho(t) dW_n(t),
$$

where

$$
\mathcal{D}[\hat{O}] \rho = \hat{O} \rho \hat{O}^\dagger - \frac{1}{2} \{\hat{O}^\dagger \hat{O}, \rho\},
$$

is the Lindblad superoperator, and

$$
\mathcal{H}[\hat{O}] \rho = \hat{O} \rho + \rho \hat{O}^\dagger - \mathrm{Tr}[\hat{O} \rho + \rho \hat{O}^\dagger] \rho,
$$

Above, $\hat{C}_i$ represent the collapse operators related to pure dissipation, while $\hat{S}_n$ are the stochastic collapse operators. The $dW_n(t)$ term is the real Wiener increment associated to $\hat{S}_n$. See [Wiseman2009Quantum](@cite) for more details.

# Arguments

  * `H`: Hamiltonian of the system $\hat{H}$. It can be either a [`QuantumObject`](@ref), a [`QuantumObjectEvolution`](@ref), or a `Tuple` of operator-function pairs.
  * `ψ0`: Initial state of the system $|\psi(0)\rangle$. It can be either a [`Ket`](@ref), [`Operator`](@ref) or [`OperatorKet`](@ref).
  * `tlist`: List of times at which to save either the state or the expectation values of the system.
  * `c_ops`: List of collapse operators $\{\hat{C}_i\}_i$. It can be either a `Vector` or a `Tuple`.
  * `sc_ops`: List of stochastic collapse operators $\{\hat{S}_n\}_n$. It can be either a `Vector`, a `Tuple` or a [`AbstractQuantumObject`](@ref). It is recommended to use the last case when only one operator is provided.
  * `e_ops`: List of operators for which to calculate expectation values. It can be either a `Vector` or a `Tuple`.
  * `params`: `NullParameters` of parameters to pass to the solver.
  * `rng`: Random number generator for reproducibility.
  * `progress_bar`: Whether to show the progress bar. Using non-`Val` types might lead to type instabilities.
  * `store_measurement`: Whether to store the measurement expectation values. Default is `Val(false)`.
  * `kwargs`: The keyword arguments for the ODEProblem.

# Notes

  * The states will be saved depend on the keyword argument `saveat` in `kwargs`.
  * If `e_ops` is empty, the default value of `saveat=tlist` (saving the states corresponding to `tlist`), otherwise, `saveat=[tlist[end]]` (only save the final state). You can also specify `e_ops` and `saveat` separately.
  * The default tolerances in `kwargs` are given as `reltol=1e-2` and `abstol=1e-2`.
  * For more details about `kwargs` please refer to [`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)

!!! tip "Performance Tip"
    When `sc_ops` contains only a single operator, it is recommended to pass only that operator as the argument. This ensures that the stochastic noise is diagonal, making the simulation faster.


# Returns

  * `prob`: The [`TimeEvolutionProblem`](@ref) containing the `SDEProblem` for the Stochastic Master Equation time evolution.
