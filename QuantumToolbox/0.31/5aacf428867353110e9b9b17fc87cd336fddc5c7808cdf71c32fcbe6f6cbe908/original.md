```
mcsolveProblem(
    H::Union{AbstractQuantumObject{Operator},Tuple},
    ψ0::QuantumObject{Ket},
    tlist::AbstractVector,
    c_ops::Union{Nothing,AbstractVector,Tuple} = nothing;
    e_ops::Union{Nothing,AbstractVector,Tuple} = nothing,
    params = NullParameters(),
    rng::AbstractRNG = default_rng(),
    jump_callback::TJC = ContinuousLindbladJumpCallback(),
    kwargs...,
)
```

Generate the ODEProblem for a single trajectory of the Monte Carlo wave function time evolution of an open quantum system.

Given a system Hamiltonian $\hat{H}$ and a list of collapse (jump) operators $\{\hat{C}_n\}_n$, the evolution of the state $|\psi(t)\rangle$ is governed by the Schrodinger equation:

$$
\frac{\partial}{\partial t} |\psi(t)\rangle= -i \hat{H}_{\textrm{eff}} |\psi(t)\rangle
$$

with a non-Hermitian effective Hamiltonian:

$$
\hat{H}_{\textrm{eff}} = \hat{H} - \frac{i}{2} \sum_n \hat{C}_n^\dagger \hat{C}_n.
$$

To the first-order of the wave function in a small time $\delta t$, the strictly negative non-Hermitian portion in $\hat{H}_{\textrm{eff}}$ gives rise to a reduction in the norm of the wave function, namely

$$
\langle \psi(t+\delta t) | \psi(t+\delta t) \rangle = 1 - \delta p,
$$

where 

$$
\delta p = \delta t \sum_n \langle \psi(t) | \hat{C}_n^\dagger \hat{C}_n | \psi(t) \rangle
$$

is the corresponding quantum jump probability.

If the environmental measurements register a quantum jump, the wave function undergoes a jump into a state defined by projecting $|\psi(t)\rangle$ using the collapse operator $\hat{C}_n$ corresponding to the measurement, namely

$$
| \psi(t+\delta t) \rangle = \frac{\hat{C}_n |\psi(t)\rangle}{ \sqrt{\langle \psi(t) | \hat{C}_n^\dagger \hat{C}_n | \psi(t) \rangle} }
$$

# Arguments

  * `H`: Hamiltonian of the system $\hat{H}$. It can be either a [`QuantumObject`](@ref), a [`QuantumObjectEvolution`](@ref), or a `Tuple` of operator-function pairs.
  * `ψ0`: Initial state of the system $|\psi(0)\rangle$.
  * `tlist`: List of times at which to save either the state or the expectation values of the system.
  * `c_ops`: List of collapse operators $\{\hat{C}_n\}_n$. It can be either a `Vector` or a `Tuple`.
  * `e_ops`: List of operators for which to calculate expectation values. It can be either a `Vector` or a `Tuple`.
  * `params`: Parameters to pass to the solver. This argument is usually expressed as a `NamedTuple` or `AbstractVector` of parameters. For more advanced usage, any custom struct can be used.
  * `rng`: Random number generator for reproducibility.
  * `jump_callback`: The Jump Callback type: Discrete or Continuous. The default is `ContinuousLindbladJumpCallback()`, which is more precise.
  * `kwargs`: The keyword arguments for the ODEProblem.

# Notes

  * The states will be saved depend on the keyword argument `saveat` in `kwargs`.
  * If `e_ops` is empty, the default value of `saveat=tlist` (saving the states corresponding to `tlist`), otherwise, `saveat=[tlist[end]]` (only save the final state). You can also specify `e_ops` and `saveat` separately.
  * The default tolerances in `kwargs` are given as `reltol=1e-6` and `abstol=1e-8`.
  * For more details about `kwargs` please refer to [`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)

# Returns

  * `prob`: The [`TimeEvolutionProblem`](@ref) containing the `ODEProblem` for the Monte Carlo wave function time evolution.
