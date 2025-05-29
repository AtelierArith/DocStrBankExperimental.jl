```julia
mutable struct DynamicsResult{T, M}
```

`Mechanism`の動力学に関連する変数を格納します。例えば、`Mechanism`の質量行列や関節加速度ベクトルなどです。

型パラメータ:

  * `T`: 動力学関連変数のスカラー型。
  * `M`: `Mechanism`のスカラー型。
