```julia
struct UAIModel{ET, FT<:(TensorInference.Factor{ET})}
```

### フィールド

  * `nvars` は変数の数です,
  * `cards` は変数のカーディナリティのベクトルです,
  * `factors` はファクターのベクトルです,
