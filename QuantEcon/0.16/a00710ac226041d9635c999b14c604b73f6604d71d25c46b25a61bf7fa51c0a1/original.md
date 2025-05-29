DiscreteDP type for specifying parameters for discrete dynamic programming model Dense Matrix Formulation

##### Parameters

  * `R::Array{T,NR}` : Reward Array
  * `Q::Array{T,NQ}` : Transition Probability Array
  * `beta::Float64`  : Discount Factor

##### Returns

  * `ddp::DiscreteDP` : Constructor for DiscreteDP object
