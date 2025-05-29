```
struct NormedProjection <: Projection
  projection::Projection
  norm_matrix::MatrixOrTensor
end
```

Represents a `Projection` `projection` spanning a space equipped with an inner product represented by the quantity `norm_matrix`
