```
sim_epidemics(
    model::EpidemicModel{SI,TG};
    patient_zero::Union{Vector{Int},Nothing}=nothing,
    γ::Union{Float64,Nothing}=nothing) where {TG<:Union{<:AbstractGraph,Vector{<:AbstractGraph}}}
```

Simulates an epidemic outbreak using the SI (Susceptible-Infectious) model.

# Arguments

  * `model`: The SI epidemic model, encapsulating information about the infection dynamics, contact graph, and other parameters.
  * `patient_zero`: (Optional) A vector specifying the indices of initial infected individuals. If not provided (default `nothing`), patient zero is selected randomly based on the probability `γ`.
  * `γ`: (Optional) The probability of being a patient zero. If `patient_zero` is not specified and `γ` is provided, patient zero is chosen randomly with probability `γ`. If both `patient_zero` and `γ` are not provided (default `nothing`), patient zero is selected randomly with equal probability for each individual.
  * `rng`: (Optional) A random number generator. Default is `Xoshiro(1234)`.

# Returns

  * A matrix representing the epidemic outbreak configuration over time. Each row corresponds to a node, and each column represents a time step. The values in the matrix indicate the state of each node at each time step: 0.0 for Susceptible (S) and 1.0 for Infected (I).
