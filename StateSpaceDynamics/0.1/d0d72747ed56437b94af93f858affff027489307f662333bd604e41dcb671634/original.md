```
fit!(model::HiddenMarkovModel, Y::Matrix{<:Real}, X::Union{Matrix{<:Real}, Nothing}=nothing; max_iters::Int=100, tol::Float64=1e-6)
```

Fit the Hidden Markov Model to multiple trials of data using the EM algorithm.

# Arguments

  * `model::HiddenMarkovModel`: The Hidden Markov Model to fit.
  * `Y::Vector{<:Matrix{<:Real}}`: The trialized emission data.
  * `X::Union{Vector{<:Matrix{<:Real}}, Nothing}=nothing`: Optional input data for fitting Switching Regression Models
  * `max_iters::Int=100`: The maximum number of iterations to run the EM algorithm.
  * `tol::Float64=1e-6`: When the log likelihood is improving by less than this value, the algorithm will stop.
