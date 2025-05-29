```julia
struct MMAPModel{LT, AT<:AbstractArray}
```

Computing the most likely assignment to the query variables,  Xₘ ⊆ X after marginalizing out the remaining variables Xₛ = X \ Xₘ.

$$
{\rm MMAP}(X_i|E=e) = \arg \max_{X_M} \sum_{X_S} \prod_{F} f(x_M, x_S, e)
$$

### Fields

  * `vars` is the query variables in the tensor network.
  * `code` is the tropical tensor network contraction pattern.
  * `tensors` is the tensors fed into the tensor network.
  * `clusters` is the clusters, each element of this cluster is a [`TensorNetworkModel`](@ref) instance for marginalizing certain variables.
  * `evidence` is a dictionary to specifiy degree of freedoms fixed to certain values, which should not have overlap with the query variables.
