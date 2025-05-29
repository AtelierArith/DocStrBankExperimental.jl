```
struct InfinitePEPO{T<:PEPOTensor}
```

Represents an infinite projected entangled-pair operator (PEPO) on a 3D cubic lattice.

## Fields

  * `A::Array{T, 3} where T<:(TensorKit.AbstractTensorMap{<:Any, S, 2, 4} where S<:TensorKit.ElementarySpace)`
