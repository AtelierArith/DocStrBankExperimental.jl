```
run_SCDC(
    model::EpidemicModel{TI,TG},
    obsprob::Function,
    γ::Float64,
    maxiter::Int64,
    epsconv::Float64,
    damp::Float64;
    μ_cutoff::Float64 = -Inf,
    n_iter_nc::Int64 = 1,
    damp_nc::Float64 = 0.0,
    callback::Function=(x...) -> nothing,
    printlog::Bool = false,
    rng::AbstractRNG=Xoshiro(1234)) where {TI<:InfectionModel,TG<:Union{<:AbstractGraph,Vector{<:AbstractGraph}}}
```

Runs the Small Coupling Dynamic Cavity (SCDC) inference algorithm.

This function performs SCDC inference on the specified epidemic model, using the provided evidence (likelihood) probability function, and other parameters such as the probability of being a patient zero, maximum number of iterations, convergence threshold, damping factor, etc. It iteratively updates cavity messages until convergence or until the maximum number of iterations is reached.

# Arguments

  * `model`: An [`EpidemicModel`](@ref) representing the epidemic model.
  * `obsprob`: A function representing the evidence (likelihood) probability p(O|x) of an observation O given the planted state x.
  * `γ`: The probability of being a patient zero.
  * `maxiter`: The maximum number of iterations.
  * `epsconv`: The convergence threshold of the algorithm.
  * `damp`: The damping factor of the algorithm.

# Keyword Arguments

  * `μ_cutoff::Float64`: Cutoff value for some parameter μ (default is -Inf).
  * `n_iter_nc::Int64`: Number of iterations for non-converging cases (default is 1).
  * `damp_nc::Float64`: Damping factor for non-converging cases (default is 0.0).
  * `callback::Function`: Callback function to be called during iterations (default does nothing).
  * `printlog::Bool`: Print log messages during the algorithm (default is false).
  * `rng::AbstractRNG`: Random number generator (default is Xoshiro).

# Returns

  * `nodes`: An array of [`Node`](@ref) objects representing the updated node states after inference.
