```
ConfigSystem(ndim::Int,gravity::Vector{Float64},num_params::NumParams)
```

この問題を定義するための追加システム情報。

## フィールド

  * `ndim`: この問題の次元。選択肢は2または3
  * `gravity`: 無次元重力。[x,y,z]方向にあります。したがって、重力が下向きの2d問題を説明している場合、[0.,-1.,0.]であるべきです。
  * `num_params`: 型`NumParams`を参照してください。
