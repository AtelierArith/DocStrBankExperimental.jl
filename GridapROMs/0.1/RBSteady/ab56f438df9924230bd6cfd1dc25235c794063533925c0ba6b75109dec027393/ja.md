```
struct NormedProjection <: Projection
  projection::Projection
  norm_matrix::MatrixOrTensor
end
```

`Projection` `projection` が内積で装備された空間を span し、`norm_matrix` で表される量を表します。
