A mutable struct representing a Matrix Product Operator (MPO) tensor in a tensor network.

## Fields

  * `top::Vector{Tensor{T, 2}}`: Vector of tensors representing the top tensor of the MPO. Empty if `N == 2`.
  * `ctr::Union{Tensor{T, N}, Nothing}`: Central tensor of the MPO. `Nothing` if not present.
  * `bot::Vector{Tensor{T, 2}}`: Vector of tensors representing the bottom tensor of the MPO. Empty if `N == 2`.
  * `dims::Dims{N}`: Dimensions of the MPO tensor.

## Description

`MpoTensor{T, N}` is a mutable struct that represents a Matrix Product Operator tensor in a tensor network.      The MPO tensor is characterized by its top and bottom tensors, a central tensor (`ctr`), and dimensions (`dims`).  The top and bottom legs are vectors of two-dimensional tensors (`Tensor{T, 2}`).  The central tensor is of type `Tensor{T, N}` or `Nothing` if not present.  The dimensions of the MPO tensor are specified by `dims`. 
