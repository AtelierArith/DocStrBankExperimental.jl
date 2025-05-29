```
sample(model::HiddenMarkovModel, data...; n::Int)
```

Generate `n` samples from a Hidden Markov Model. Returns a tuple of the state sequence and the observation sequence.

# Arguments

  * `model::HiddenMarkovModel`: The Hidden Markov Model to sample from.
  * `data...`: The data to fit the Hidden Markov Model. Requires the same format as the emission model.
  * `n::Int`: The number of samples to generate.

# Returns

  * `state_sequence::Vector{Int}`: The state sequence, where each element is an integer 1:K.
  * `observation_sequence::Matrix{Float64}`: The observation sequence. This takes the form of the emission model's output.
