```julia
MixtureDensityNetwork(
    input::Int64,
    output::Int64,
    layers::Vector{Int64},
    mixtures::Int64
) -> Union{MixtureDensityNetworks.MixtureDensityNetwork{MixtureDensityNetworks.MultivariateGMM}, MixtureDensityNetworks.MixtureDensityNetwork{MixtureDensityNetworks.UnivariateGMM}}

```

標準的な混合密度ネットワークを構築します。

# パラメータ

  * `input`: 入力特徴の次元。
  * `output`: 出力の次元。output = 1に設定すると単変量モデルを示し、output > 1は多変量モデルを示します。
  * `layers`: 最初の層から始まる隠れ層のトポロジー。
  * `mixtures`: 予測分布に使用するガウス混合の数。
