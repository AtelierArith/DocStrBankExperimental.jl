```
SwitchingGaussianRegression(; 
    K::Int,
    input_dim::Int,
    output_dim::Int,
    include_intercept::Bool = true,
    β::Matrix{<:Real} = if include_intercept
        zeros(input_dim + 1, output_dim)
    else
        zeros(input_dim, output_dim)
    end,
    Σ::Matrix{<:Real} = Matrix{Float64}(I, output_dim, output_dim),
    λ::Float64 = 0.0,
    A::Matrix{<:Real} = initialize_transition_matrix(K),
    πₖ::Vector{Float64} = initialize_state_distribution(K)
)
```

Create a Switching Gaussian Regression Model

# Arguments

  * `K::Int`: The number of hidden states.
  * `input_dim::Int`: The dimensionality of the input features.
  * `output_dim::Int`: The dimensionality of the output predictions.
  * `include_intercept::Bool`: Whether to include an intercept in the regression model (default is `true`).
  * `β::Matrix{<:Real}`: The regression coefficients (defaults to zeros based on `input_dim` and `output_dim`).
  * `Σ::Matrix{<:Real}`: The covariance matrix of the Gaussian emissions (defaults to an identity matrix).
  * `λ::Float64`: The regularization parameter for the regression (default is `0.0`).
  * `A::Matrix{<:Real}`: The transition matrix of the Hidden Markov Model (defaults to random initialization).
  * `πₖ::Vector{Float64}`: The initial state distribution of the Hidden Markov Model (defaults to random initialization).

# Returns

  * `::HiddenMarkovModel`: A Switching Gaussian Regression Model
