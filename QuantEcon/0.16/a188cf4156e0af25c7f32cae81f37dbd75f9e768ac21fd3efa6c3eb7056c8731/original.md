Simulate one sample path of the Markov chain `mc`. The resulting vector has the indices of the state values of `mc` as elements.

### Arguments

  * `mc::MarkovChain` : MarkovChain instance.
  * `ts_length::Int` : Length of simulation
  * `;init::Int=rand(1:n_states(mc))` : Initial state

### Returns

  * `X::Vector{Int}` : Vector containing the sample path, with length ts_length
