```julia
UnivariateGMM(
    input::Int64,
    mixtures::Int64
) -> MixtureDensityNetworks.UnivariateGMM

```

ユニバリアントガウス混合モデルを出力として返すレイヤーを構築します。

# パラメータ

  * `input`: 特徴ベクトルの長さを指定します。このレイヤーは、`input x N` の次元を持つ行列を入力として期待します。
  * `mixtures`: GMMで使用する混合の数。
