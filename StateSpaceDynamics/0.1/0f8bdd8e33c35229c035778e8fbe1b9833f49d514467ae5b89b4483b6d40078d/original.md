```
SwitchingBernoulliRegression(; K::Int, input_dim::Int, include_intercept::Bool=true, β::Vector{<:Real}=if include_intercept zeros(input_dim + 1) else zeros(input_dim) end, λ::Float64=0.0, A::Matrix{<:Real}=initialize_transition_matrix(K), πₖ::Vector{Float64}=initialize_state_distribution(K))
```

Create a Switching Bernoulli Regression Model

# Arguments

  * `K::Int`: The number of hidden states.
  * `input_dim::Int`: The dimensionality of the input data.
  * `include_intercept::Bool=true`: Whether to include an intercept in the regression model (defaults to true).
  * `β::Vector{<:Real}`: The regression coefficients (defaults to zeros).
  * `λ::Float64=0.0`: Regularization parameter for the regression (defaults to zero).
  * `A::Matrix{<:Real}=initialize_transition_matrix(K)`: The transition matrix of the HMM (defaults to random initialization).
  * `πₖ::Vector{Float64}=initialize_state_distribution(K)`: The initial state distribution of the HMM (defaults to random initialization).

# Returns

  * `::HiddenMarkovModel`: A Switching Bernoulli Regression Model
