```
ResNet(layer_sizes::NTuple{N, Int}, activation; outermost=true,
               init_weight=kaiming_uniform(activation),
               init_bias=zeros32,
               allow_fast_activation=false)
ResNet(in_dims::Int, out_dims::Int, activation::Function;
               hidden_dims::Int, num_layers::Int, outermost=true,
               init_weight=kaiming_uniform(activation),
               init_bias=zeros32,
               allow_fast_activation=false)
```

完全結合層を作成します。

## 引数

  * `layer_sizes`: 各層の次元数。
  * `hidden_dims`: 隠れ次元の数。
  * `num_layers`: 層の数。
  * `activation`: 活性化関数。

## キーワード引数

  * `outermost`: 最後の層に活性化関数を使用するかどうか。`false`の場合、活性化関数は最後の層の出力に適用されます。
  * `init_weight`: 重みの初期化方法。
  * `allow_fast_activation`: `true`の場合、特定の活性化がより高速なバージョンで近似できます。新しい活性化関数はNNlib.fast_act(activation)によって与えられます。

## 例

```julia
julia> ResNet((1, 12, 24, 32), relu)
Chain(
    layer_1 = Dense(1 => 12, relu),     # 24 parameters
    layer_2 = SkipConnection(
        Dense(12 => 24, relu),          # 312 parameters
        +
    ),
    layer_3 = Dense(24 => 32),          # 800 parameters
)         # Total: 1_136 parameters,
          #        plus 0 states, summarysize 48 bytes.

julia> ResNet(1, 10, relu; hidden_dims=20, num_layers=3)
Chain(
    layer_1 = Dense(1 => 20, relu),     # 40 parameters
    layer_2 = SkipConnection(
        Dense(20 => 20, relu),          # 420 parameters
        +
    ),
    layer_3 = SkipConnection(
        Dense(20 => 20, relu),          # 420 parameters
        +
    ),
    layer_4 = Dense(20 => 10),          # 210 parameters
)         # Total: 1_090 parameters,
          #        plus 0 states, summarysize 64 bytes.
```
