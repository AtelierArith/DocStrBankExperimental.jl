```
AbstractTensor{T,S,N} = AbstractTensorMap{T,S,N,0}
```

Abstract supertype of all tensors, i.e. elements in the tensor product space of type `ProductSpace{S, N}`, with element type `T`.

An `AbstractTensor{T, S, N}` is actually a special case `AbstractTensorMap{T, S, N, 0}`, i.e. a tensor map with only non-trivial output spaces.
