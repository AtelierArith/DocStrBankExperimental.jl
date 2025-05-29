```
BoxForward{AMA<:ForwardAlgorithm} <: ForwardAlgorithm
```

Forward algorithm that uses a box approximation for non-identity activations and applies the affine map according to the specified algorithm.

### Fields

  * `affine_map_algorithm` – algorithm to apply for affine maps
