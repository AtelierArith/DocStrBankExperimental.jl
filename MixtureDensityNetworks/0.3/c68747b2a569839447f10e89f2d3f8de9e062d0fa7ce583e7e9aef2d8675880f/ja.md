```julia
predict_mode(
    m::MixtureDensityNetworks.MixtureDensityNetwork,
    X::Matrix{<:Real}
) -> Any

```

条件付き分布 P(Y|X) における最も高い確率に関連する点を予測します。

# パラメータ

  * `m`: 予測を生成するためのモデル。
  * `X`: `m` に渡される入力。n は観測の数であり、dxn の次元を持つ行列であることが期待されます。

# 戻り値

`m(X)` によって返される各分布のモード。
