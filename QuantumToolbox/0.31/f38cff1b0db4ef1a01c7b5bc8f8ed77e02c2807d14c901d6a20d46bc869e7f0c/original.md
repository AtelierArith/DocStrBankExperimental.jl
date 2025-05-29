```
ssesolveEnsembleProblem(
    H::Union{AbstractQuantumObject{Operator},Tuple},
    ψ0::QuantumObject{Ket},
    tlist::AbstractVector,
    sc_ops::Union{Nothing,AbstractVector,Tuple,AbstractQuantumObject} = nothing;
    e_ops::Union{Nothing,AbstractVector,Tuple} = nothing,
    params = NullParameters(),
    rng::AbstractRNG = default_rng(),
    ntraj::Int = 500,
    ensemblealg::EnsembleAlgorithm = EnsembleThreads(),
    prob_func::Union{Function, Nothing} = nothing,
    output_func::Union{Tuple,Nothing} = nothing,
    progress_bar::Union{Val,Bool} = Val(true),
    store_measurement::Union{Val,Bool} = Val(false),
    kwargs...,
)
```

Generate the SDE EnsembleProblem for the Stochastic Schrödinger time evolution of a quantum system. This is defined by the following stochastic differential equation:

$$
d|\psi(t)\rangle = -i \hat{K} |\psi(t)\rangle dt + \sum_n \hat{M}_n |\psi(t)\rangle dW_n(t)
$$

where 

$$
\hat{K} = \hat{H} + i \sum_n \left(\frac{e_n}{2} \hat{S}_n - \frac{1}{2} \hat{S}_n^\dagger \hat{S}_n - \frac{e_n^2}{8}\right),
$$

$$
\hat{M}_n = \hat{S}_n - \frac{e_n}{2},
$$

and

$$
e_n = \langle \hat{S}_n + \hat{S}_n^\dagger \rangle.
$$

Above, $\hat{S}_n$ are the stochastic collapse operators and  $dW_n(t)$ is the real Wiener increment associated to $\hat{S}_n$. See [Wiseman2009Quantum](@cite) for more details.

# Arguments

  * `H`: Hamiltonian of the system $\hat{H}$. It can be either a [`QuantumObject`](@ref), a [`QuantumObjectEvolution`](@ref), or a `Tuple` of operator-function pairs.
  * `ψ0`: Initial state of the system $|\psi(0)\rangle$.
  * `tlist`: List of times at which to save either the state or the expectation values of the system.
  * `sc_ops`: List of stochastic collapse operators $\{\hat{S}_n\}_n$. It can be either a `Vector`, a `Tuple` or a [`AbstractQuantumObject`](@ref). It is recommended to use the last case when only one operator is provided.
  * `e_ops`: List of operators for which to calculate expectation values. It can be either a `Vector` or a `Tuple`.
  * `params`: `NullParameters` of parameters to pass to the solver.
  * `rng`: Random number generator for reproducibility.
  * `ntraj`: Number of trajectories to use. Default is `500`.
  * `ensemblealg`: Ensemble method to use. Default to `EnsembleThreads()`.
  * `jump_callback`: The Jump Callback type: Discrete or Continuous. The default is `ContinuousLindbladJumpCallback()`, which is more precise.
  * `prob_func`: Function to use for generating the SDEProblem.
  * `output_func`: a `Tuple` containing the `Function` to use for generating the output of a single trajectory, the (optional) `ProgressBar` object, and the (optional) `RemoteChannel` object.
  * `progress_bar`: Whether to show the progress bar. Using non-`Val` types might lead to type instabilities.
  * `store_measurement`: Whether to store the measurement results. Default is `Val(false)`.
  * `kwargs`: The keyword arguments for the ODEProblem.

# Notes

  * The states will be saved depend on the keyword argument `saveat` in `kwargs`.
  * If `e_ops` is empty, the default value of `saveat=tlist` (saving the states corresponding to `tlist`), otherwise, `saveat=[tlist[end]]` (only save the final state). You can also specify `e_ops` and `saveat` separately.
  * The default tolerances in `kwargs` are given as `reltol=1e-2` and `abstol=1e-2`.
  * For more details about `kwargs` please refer to [`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)

!!! tip "Performance Tip"
    When `sc_ops` contains only a single operator, it is recommended to pass only that operator as the argument. This ensures that the stochastic noise is diagonal, making the simulation faster.


# Returns

  * `prob::EnsembleProblem with SDEProblem`: The Ensemble SDEProblem for the Stochastic Shrödinger time evolution.
