```julia
struct UAIModel{ET, FT<:(TensorInference.Factor{ET})}
```

### フィールド

  * `nvars` は変数の数です,
  * `cards` は変数のための基数のベクトルです,
  * `factors` は因子のベクトルです,
