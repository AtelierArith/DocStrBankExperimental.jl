```
function class_probabilities(model::HiddenMarkovModel, Y::Vector{<:Matrix{<:Real}}, X::Union{Vector{<:Matrix{<:Real}},Nothing}=nothing;)
```

Calculate the class probabilities at each time point using forward backward algorithm on multiple trials of data

# Arguments

  * `model::HiddenMarkovModel`: The Hidden Markov Model to fit.
  * `Y::Vectpr{<:Matrix{<:Real}}`: The trials of emission data
  * `X::Union{Vector{<:Matrix{<:Real}},Nothing}=nothing`: Optional trials of input data for fitting Switching Regression Models

# Returns

  * `class_probabilities::Vector{<:Matrix{Float64}}`: Each trial's class probabilities at each timepoint
