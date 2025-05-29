```
function class_probabilities(model::HiddenMarkovModel, Y::Matrix{<:Real}, X::Union{Matrix{<:Real},Nothing}=nothing;)
```

Calculate the class probabilities at each time point using forward backward algorithm

# Arguments

  * `model::HiddenMarkovModel`: The Hidden Markov Model to fit.
  * `Y::Matrix{<:Real}`: The emission data
  * `X::Union{Matrix{<:Real},Nothing}=nothing`: Optional input data for fitting Switching Regression Models

# Returns

  * `class_probabilities::Matrix{Float64}`: The class probabilities at each timepoint
