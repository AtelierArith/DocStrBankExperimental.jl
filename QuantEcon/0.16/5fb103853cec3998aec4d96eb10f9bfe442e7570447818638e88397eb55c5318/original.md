Compute the value of a policy.

##### Parameters

  * `ddp::DiscreteDP` : Object that contains the model parameters
  * `sigma::AbstractVector{T<:Integer}` : Policy rule vector

##### Returns

  * `v_sigma::Array{Float64}` : Value vector of `sigma`, of length `n`.
