```
ShiftInvariantWaveletTransformObject{N, T₁<:Integer, T₂<:AbstractFloat}
```

Data structure to hold all shift-invariant wavelet transform (SIWT) information of a signal.

# Parameters

  * `Nodes::Dict{NTuple{3,T₁}, ShiftInvariantWaveletTransformNode{N,T₁,T₂}}`: Dictionary containing the information of each node within a tree.
  * `SignalSize::Union{T₁, NTuple{N,T₁}}`: Size of the original signal.
  * `MaxTransformLevel::T₁`: Maximum levels of transform set for signal.
  * `Wavelet::OrthoFilter`: A discrete wavelet for transform purposes.
  * `MinCost::Union{T₂, Nothing}`: The current minimum [`ShannonEntropyCost`](@ref) cost of  the decomposition tree.

!!! note
    `MinCost` parameter will contain the cost of the root node by default. To compute the  true minimum cost of the decomposition tree, one will need to first compute the SIWT best basis by calling [`bestbasistree`](@ref).


  * `BestTree::Vector{NTuple{3,T₁}}`: A collection of node indices that belong in the best basis tree.

!!! note
    `BestTree` parameter will contain all the nodes by default, ie. the full decomposition  will be the best tree. To get the SIWT best basis tree that produce the minimum cost,  one will neeed to call [`bestbasistree`](@ref).


**See also:** [`ShiftInvariantWaveletTransformNode`](@ref)
