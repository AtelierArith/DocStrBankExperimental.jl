Finite-state discrete-time Markov chain.

Methods are available that provide useful information such as the stationary distributions, and communication and recurrent classes, and allow simulation of state transitions.

##### Fields

  * `p::AbstractMatrix` : The transition matrix. Must be square, all elements must be nonnegative, and all rows must sum to unity.
  * `state_values::AbstractVector` : Vector containing the values associated with the states.
