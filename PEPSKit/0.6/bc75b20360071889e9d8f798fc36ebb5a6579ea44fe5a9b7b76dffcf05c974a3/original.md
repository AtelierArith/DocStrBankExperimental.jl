```
struct InfinitePartitionFunction{T<:PartitionFunctionTensor}
```

Represents an infinite partition function on a 2D square lattice.

## Fields

  * `A::Matrix{T} where T<:(TensorKit.AbstractTensorMap{<:Any, S, 2, 2} where S<:TensorKit.ElementarySpace)`
