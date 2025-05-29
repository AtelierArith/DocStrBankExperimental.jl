DiscreteDP type for specifying parameters for discrete dynamic programming model State-Action Pair Formulation

##### Parameters

  * `R::Array{T,NR}` : Reward Array
  * `Q::Array{T,NQ}` : Transition Probability Array
  * `beta::Float64`  : Discount Factor
  * `s_indices::Vector{Tind}`: State Indices. Empty unless using SA formulation
  * `a_indices::Vector{Tind}`: Action Indices. Empty unless using SA formulation
  * `a_indptr::Vector{Tind}`: Action Index Pointers. Empty unless using SA formulation

##### Returns

  * `ddp::DiscreteDP` : Constructor for DiscreteDP object
