```
viterbi(model::HiddenMarkovModel, Y::Vector{<:Matrix{<:Real}}, X::Union{Vector{<:Matrix{<:Real}},Nothing}=nothing;)
```

Get most likely class labels using the Viterbi algorithm for multiple trials of data

# Arguments

  * `model::HiddenMarkovModel`: The Hidden Markov Model to fit.
  * `Y::Vectpr{<:Matrix{<:Real}}`: The trials of emission data
  * `X::Union{Vector{<:Matrix{<:Real}},Nothing}=nothing`: Optional trials of input data for fitting Switching Regression Models

# Returns

  * `best_path::Vector{<:Vector{Float64}}`: Each trial's best state path
