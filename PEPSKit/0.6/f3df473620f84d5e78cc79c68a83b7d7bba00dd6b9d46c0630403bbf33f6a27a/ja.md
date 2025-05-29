```julia
struct SimpleUpdate
```

無限PEPSのボンド重みを持つ単純更新（SU）のアルゴリズム構造体。各SUの実行は、特異値の差が`tol`より小さくなると収束したと見なされる。

## フィールド

  * `dt::Float64`
  * `tol::Float64`
  * `maxiter::Int64`
  * `trscheme::TensorKit.TruncationScheme`
