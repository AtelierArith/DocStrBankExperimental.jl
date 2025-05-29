```
amplitude_matrix(axi::AxisymmetricTransitionMatrix{CT, N, V, T}, ϑᵢ, φᵢ, ϑₛ, φₛ;
                          λ = 2π,
                          rot::Union{Nothing, Rotation{3}} = nothing) where {CT, N, V, T}
```

軸対称散乱体の振幅行列を計算します。

パラメータ:

  * `axi`: 散乱体のT行列。
  * `ϑᵢ`: 入射波の天頂角。
  * `φᵢ`: 入射波の方位角。
  * `ϑₛ`: 散乱波の天頂角。
  * `φₛ`: 散乱波の方位角。
  * `λ`: ホスト媒質における入射波の波長。デフォルトは2π。
  * `rot`: 散乱体の回転。
