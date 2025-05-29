```
viterbi(model::HiddenMarkovModel, Y::Matrix{<:Real}, X::Union{Matrix{<:Real},Nothing}=nothing;)
```

Get most likely class labels using the Viterbi algorithm

# Arguments

  * `model::HiddenMarkovModel`: The Hidden Markov Model to fit.
  * `Y::Matrix{<:Real}`: The emission data
  * `X::Union{Matrix{<:Real},Nothing}=nothing`: Optional input data for fitting Switching Regression Models

# Returns

  * `best_path::Vector{Float64}`: The most likely state label at each timepoint
