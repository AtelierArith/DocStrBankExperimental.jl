The Bellman operator, which computes and returns the updated value function $Tv$ for a given value function $v$.

This function will fill the input `v` with `Tv` and the input `sigma` with the corresponding policy rule.

##### Parameters

  * `ddp::DiscreteDP`: The ddp model
  * `v::AbstractVector{T<:AbstractFloat}`: The current guess of the value function. This array will be overwritten
  * `sigma::AbstractVector`: A buffer array to hold the policy function. Initial values not used and will be overwritten

##### Returns

  * `Tv::Vector`: Updated value function vector
  * `sigma::typeof(sigma)`: Policy rule
