```
evolve_fluctuations(problem::Problem, τ::Real, β::Vector{<:Real}, γ::Vector{<:Real})
```

### Input

  * `problem::Problem`: A `Problem` instance defining the optimization problem.
  * `τ::Real`: The time-step of the considered annealing schedule.
  * `β::Vector{<:Real}`: The corresponding vector of QAOA driver parameters.
  * `γ::Vector{<:Real}`: The corresponding vector of QAOA problem parameters.

### Output

  * The Lyapunov exponents characterizing the dynamics of the Gaussian fluctuations.
