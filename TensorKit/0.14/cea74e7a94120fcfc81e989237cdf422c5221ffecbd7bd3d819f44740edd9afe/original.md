```
⊗(t1::AbstractTensorMap, t2::AbstractTensorMap, ...) -> TensorMap
otimes(t1::AbstractTensorMap, t2::AbstractTensorMap, ...) -> TensorMap
```

Compute the tensor product between two `AbstractTensorMap` instances, which results in a new `TensorMap` instance whose codomain is `codomain(t1) ⊗ codomain(t2)` and whose domain is `domain(t1) ⊗ domain(t2)`.
