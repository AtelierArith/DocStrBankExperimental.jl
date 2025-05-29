```
HiddenMarkovModel
```

A Hidden Markov Model (HMM) with custom emissions.

# Fields

  * `K::Int`: Number of states.
  * `B::Vector=Vector()`: Vector of emission models.
  * `emission=nothing`: If B is missing emissions, clones of this model will be used to fill in the rest.
  * `A::Matrix{<:Real}`: Transition matrix.
  * `πₖ::Vector{Float64}`: Initial state distribution.
