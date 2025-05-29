```
GaussianHMM(; K::Int, output_dim::Int, A::Matrix{<:Real}=initialize_transition_matrix(K), πₖ::Vector{Float64}=initialize_state_distribution(K))
```

Create a Hidden Markov Model with Gaussian Emissions

# Arguments

  * `K::Int`: The number of hidden states
  * `output_dim::Int`: The dimensionality of the observation
  * `A::Matrix{<:Real}=initialize_transition_matrix(K)`: The transition matrix of the HMM (defaults to random initialization)
  * `πₖ::Vector{Float64}=initialize_state_distribution(K)`: The initial state distribution of the HMM (defaults to random initialization)

# Returns

  * `::HiddenMarkovModel`: Hidden Markov Model Object with Gaussian Emissions

```
