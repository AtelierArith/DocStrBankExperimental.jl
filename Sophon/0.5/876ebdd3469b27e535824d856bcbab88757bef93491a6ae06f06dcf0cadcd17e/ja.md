```
FourierAttention(in_dims::Int, out_dims::Int, activation::Function, std;
                 hidden_dims::Int=512, num_layers::Int=6, modes::NTuple)
FourierAttention(in_dims::Int, out_dims::Int, activation::Function, frequencies;
                 hidden_dims::Int=512, num_layers::Int=6, modes::NTuple)
```

[`FourierFeature`](@ref) と [`PINNAttention`](@ref) を組み合わせたモデルです。

```
x → [FourierFeature(x); x] → PINNAttention
```

## 引数

  * `in_dims`: 入力次元。

      * `out_dims`: 出力次元。
      * `activation`: 活性化関数。
      * `std`: [`FourierFeature`](@ref) を参照してください。
      * `frequencies`: [`FourierFeature`](@ref) を参照してください。

## キーワード引数

  * `hidden_dim`: 各隠れ層の隠れ次元。
  * `num_layers`: 隠れ層の数。

## 例

```julia
julia> FourierAttention(3, 1, sin, (1 => 10, 10 => 10, 50 => 10); hidden_dims=10, num_layers=3)
Chain(
    layer_1 = SkipConnection(
        FourierFeature(3 => 60),
        vcat
    ),
    layer_2 = PINNAttention(
        H_net = Dense(63 => 10, sin),   # 640 パラメータ
        U_net = Dense(63 => 10, sin),   # 640 パラメータ
        V_net = Dense(63 => 10, sin),   # 640 パラメータ
        fusion = TriplewiseFusion(
            layers = (layer_1 = Dense(10 => 10, sin), layer_2 = Dense(10 => 10, sin), layer_3 = Dense(10 => 10, sin), layer_4 = Dense(10 => 10, sin)),  # 440 パラメータ
        ),
    ),
    layer_3 = Dense(10 => 1),           # 11 パラメータ
)         # 合計: 2_371 パラメータ,
          #        さらに 90 ステート、サマリーサイズ 192 バイト
```
