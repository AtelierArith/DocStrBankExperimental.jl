```
generate(Q, n; dt=1, initial_condition=rand(1:size(Q)[1]))
```

Generate a Markov chain of length `n` with transition matrix `Q` and time step `dt`.

# Arguments

  * `Q::AbstractMatrix`: The transition matrix or generator of the Markov chain.
  * `n::Int`: The length of the Markov chain.
  * `dt::Real=1`: The time step of the Markov chain.
  * `initial_condition::Int=rand(1:size(Q)[1])`: The initial condition of the Markov chain.

# Keyword Arguments

  * `progress::Bool=false`: Whether to show a progress bar.

# Returns

  * `Vector{Int}`: A Markov chain of length `n` generated by transition matrix `Q` and time step `dt`.
