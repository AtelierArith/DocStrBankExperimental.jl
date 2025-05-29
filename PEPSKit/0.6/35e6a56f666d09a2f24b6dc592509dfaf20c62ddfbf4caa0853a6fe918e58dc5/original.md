```
struct InfinitePEPS{T<:PEPSTensor}
```

Represents an infinite projected entangled-pair state on a 2D square lattice.

## Fields

  * `A::Matrix{T} where T<:(TensorKit.AbstractTensorMap{<:Any, S, 1, 4} where S<:TensorKit.ElementarySpace)`
