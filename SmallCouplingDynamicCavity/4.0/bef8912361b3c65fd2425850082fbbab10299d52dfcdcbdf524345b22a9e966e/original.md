```
run_SCDC!(
    nodes::Vector{Node{TI,TG}}, 
    model::EpidemicModel{TI,TG}, 
    γ::Float64, 
    maxiter::Vector{Int64}, 
    epsconv::Float64, 
    damp::Vector{Float64}; 
    μ_cutoff::Float64 = -Inf, 
    n_iter_nc::Int64 = 1, 
    damp_nc::Float64 = 0.0, 
    callback::Function=(x...) -> nothing, 
    printlog::Bool = false,
    rng::AbstractRNG=Xoshiro(1234)) where {TI<:InfectionModel,TG<:Union{<:AbstractGraph,Vector{<:AbstractGraph}}}
```

Run the SCDC algorithm for epidemic modeling. The algorithm resumes the message-passing iterations from the current state of the nodes.

This function performs SCDC inference on the specified epidemic model, using the provided evidence (likelihood) probability function, and other parameters such as the probability of being a patient zero, maximum number of iterations, convergence threshold, damping factor, etc. It iteratively updates cavity messages until convergence or until the maximum number of iterations is reached. It implements a dumping schedule for the damping factor, where the dumping factor is changed after a certain number of iterations, specified by the `maxiter` and `damp` arguments.

# Arguments

  * `nodes::Vector{Node{TI,TG}}`: Vector of nodes in the epidemic model.
  * `model::EpidemicModel{TI,TG}`: The epidemic model to be used.
  * `γ::Float64`: A parameter for the algorithm (e.g., infection rate).
  * `maxiter::Vector{Int64}`: Maximum number of iterations for the algorithm.
  * `epsconv::Float64`: Convergence threshold for the algorithm.
  * `damp::Vector{Float64}`: Damping factors for the algorithm.

# Keyword Arguments

  * `μ_cutoff::Float64`: Cutoff value for some parameter μ (default is -Inf).
  * `n_iter_nc::Int64`: Number of iterations for non-converging cases (default is 1).
  * `damp_nc::Float64`: Damping factor for non-converging cases (default is 0.0).
  * `callback::Function`: Callback function to be called during iterations (default does nothing).
  * `printlog::Bool`: Print log messages during the algorithm (default is false).
  * `rng::AbstractRNG`: Random number generator (default is Xoshiro).
