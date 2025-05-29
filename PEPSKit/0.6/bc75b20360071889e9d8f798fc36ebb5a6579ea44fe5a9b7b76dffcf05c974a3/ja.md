```
struct InfinitePartitionFunction{T<:PartitionFunctionTensor}
```

2D正方格子上の無限分割関数を表します。

## フィールド

  * `A::Matrix{T} where T<:(TensorKit.AbstractTensorMap{<:Any, S, 2, 2} where S<:TensorKit.ElementarySpace)`
