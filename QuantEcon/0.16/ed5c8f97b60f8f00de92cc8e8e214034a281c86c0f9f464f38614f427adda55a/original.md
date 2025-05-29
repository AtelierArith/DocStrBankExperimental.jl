DiscreteDP type for specifying paramters for discrete dynamic programming model

##### Parameters

  * `R::Array{T,NR}` : Reward Array
  * `Q::Array{T,NQ}` : Transition Probability Array
  * `beta::Float64`  : Discount Factor
  * `a_indices::Vector{Tind}`: Action Indices. Empty unless using SA formulation
  * `a_indptr::Vector{Tind}`: Action Index Pointers. Empty unless using SA formulation

##### Returns

  * `ddp::DiscreteDP` : DiscreteDP object
