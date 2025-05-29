Given a policy `sigma`, return the reward vector `R_sigma` and the transition probability matrix `Q_sigma`.

##### Parameters

  * `ddp::DiscreteDP` : Object that contains the model parameters
  * `sigma::AbstractVector{Int}`: policy rule vector

##### Returns

  * `R_sigma::Array{Float64}`: Reward vector for `sigma`, of length `n`.
  * `Q_sigma::Array{Float64}`: Transition probability matrix for `sigma`, of shape `(n, n)`.
