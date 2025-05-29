```julia
struct TensorNetworkModel{ET, MT<:AbstractArray}
```

Probabilistic modeling with a tensor network.

### Fields

  * `nvars` are the number of variables in the tensor network.
  * `code` is the tensor network contraction pattern.
  * `tensors` are the tensors fed into the tensor network, the leading tensors are unity tensors associated with `unity_tensors_labels`.
  * `evidence` is a dictionary used to specify degrees of freedom that are fixed to certain values.
  * `unity_tensors_idx` is a vector of indices of the unity tensors in the `tensors` array. Unity tensors are dummy tensors used to obtain the marginal probabilities.
