```
Tensor{T}
```

A tensor in a network with index labels of type T.

# Fields

  * `adj::Vector{T}`: the labels of the adjacent tensors
  * `arr::Array{Float64}`: the contents of the tensor
  * `x::Float64`, `y::Float64`: position coordinates of the tensor

The order with which the neighbours are labelled in `adj` may be arbitrary, but must be compatible with the labelling of the indices of `arr`.
