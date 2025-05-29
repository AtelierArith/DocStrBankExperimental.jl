```
LabelledTensorNetwork{T}
```

A tensor network with tensor labels of type `T`. Alias for `Dict{T,Tensor{T}}`. Due to the potential performacne overheads associated with dealing with arbitrarily labelled tensors the alternative `TensorNetwork` type should be used in performance sensitive circumstances.
