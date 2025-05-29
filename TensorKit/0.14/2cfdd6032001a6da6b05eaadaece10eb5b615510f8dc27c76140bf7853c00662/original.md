```
Tensor{T, S, N, A<:DenseVector{T}} = TensorMap{T, S, N, 0, A}
```

Specific subtype of [`AbstractTensor`](@ref) for representing tensors whose data is stored in a dense vector.

A `Tensor{T, S, N, A}` is actually a special case `TensorMap{T, S, N, 0, A}`, i.e. a tensor map with only a non-trivial output space.
