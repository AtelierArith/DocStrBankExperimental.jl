```
FourierNet(ayer_sizes::NTuple, activation, modes::NTuple)
```

[`FourierFeature`](@ref) と [`FullyConnected`](@ref) を組み合わせたモデルです。

```
x → FourierFeature → FullyConnected → y
```

# 引数

  * `in_dims`: 入力次元の数。
  * `layer_sizes`: `FullyConnected` を構築するために使用される隠れ次元のタプル。
  * `activation`: `FullyConnected` を構築するために使用される活性化関数。
  * `modes`: `FourierFeature` を構築するために使用されるモードのタプル。

# 例

```julia
julia> FourierNet((2, 30, 30, 1), sin, (1 => 10, 10 => 10, 50 => 10))
Chain(
    layer_1 = FourierFeature(2 => 60),
    layer_2 = Dense(60 => 30, sin),     # 1_830 パラメータ
    layer_3 = Dense(30 => 30, sin),     # 930 パラメータ
    layer_4 = Dense(30 => 1),           # 31 パラメータ
)         # 合計: 2_791 パラメータ,
          #        さらに 60 ステート, サマリーサイズ 112 バイト。

julia> FourierNet((2, 30, 30, 1), sin, (1, 2, 3, 4))
Chain(
    layer_1 = FourierFeature(2 => 16),
    layer_2 = Dense(16 => 30, sin),     # 510 パラメータ
    layer_3 = Dense(30 => 30, sin),     # 930 パラメータ
    layer_4 = Dense(30 => 1),           # 31 パラメータ
)         # 合計: 1_471 パラメータ,
          #        さらに 4 ステート, サマリーサイズ 96 バイト。
```
