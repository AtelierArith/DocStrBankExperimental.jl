```julia
MultivariateGMM(
    input::Int64,
    output::Int64,
    mixtures::Int64
) -> MixtureDensityNetworks.MultivariateGMM

```

多変量ガウス混合モデルを出力として返すレイヤーを構築します。

# パラメータ

  * `input`: 特徴ベクトルの長さを指定します。このレイヤーは、`input x N`の次元を持つ行列を入力として期待します。
  * `output`: ラベルベクトルの長さを指定します。このレイヤーは、`output x N`の次元を持つ行列を出力として返します。
  * `mixtures`: GMMで使用する混合の数です。
