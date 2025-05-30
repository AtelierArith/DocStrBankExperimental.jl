```
PINN(chain, rng::AbstractRNG=Random.default_rng())
PINN(rng::AbstractRNG=Random.default_rng(); kwargs...)
```

ニューラルネットワーク、その状態、および初期パラメータのコンテナです。パラメータのデフォルト要素タイプは `Float64` です。

## フィールド

  * `phi`: ニューラルネットワークが1つだけの場合は [`ChainState`](@ref)、複数のニューラルネットワークがある場合は [`ChainState`](@ref) の名前付きタプルです。名前はPDEの従属変数と同じです。
  * `init_params`: ニューラルネットワークの初期パラメータです。

## 引数

  * `chain`: `AbstractExplicitLayer` または `AbstractExplicitLayer` の名前付きタプル。
  * `rng`: ニューラルネットワークの初期化に使用する `AbstractRNG`。シードを設定したい場合は、次のように書きます。

```julia
using Random
rng = Random.default_rng()
Random.seed!(rng, 0)d
```

そして、`rng` を `PINN` に渡します。

```julia
using Sophon

chain = FullyConnected((1, 6, 6, 1), sin);

# 単純な従属変数
pinn = PINN(chain, rng);

# 複数の従属変数
pinn = PINN(rng; a=chain, b=chain);
```
