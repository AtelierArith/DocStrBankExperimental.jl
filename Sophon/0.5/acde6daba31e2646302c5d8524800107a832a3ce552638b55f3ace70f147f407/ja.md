```
Siren(in_dims::Int, out_dims::Int; hidden_dims::Int, num_layers::Int, omega=30.0f0,
      init_weight=nothing))
Siren(layer_sizes::Int...; omega=30.0f0, init_weight=nothing)
```

正弦表現ネットワーク。

## キーワード引数

  * `omega`: 最初の層に使用される `ω₀`。
  * `init_weight`: **入力**層の重みの初期化アルゴリズム。すべての隠れ層は `kaiming_uniform` を初期化アルゴリズムとして使用します。デフォルトは

    $$
        W\sim \mathcal{U}\left(-\frac{\omega}{fan_{in}}, \frac{\omega}{fan_{in}}\right)
    $$

## 例

```julia
julia> Siren(2, 32, 32, 1; omega=5.0f0)
Chain(
    layer_1 = Dense(2 => 32, sin),      # 96 パラメータ
    layer_2 = Dense(32 => 32, sin),     # 1_056 パラメータ
    layer_3 = Dense(32 => 1),           # 33 パラメータ
)         # 合計: 1_185 パラメータ,
          #        0 ステート, サマリーサイズ 48 バイト.

julia> Siren(3, 1; hidden_dims=20, num_layers=3)
Chain(
    layer_1 = Dense(3 => 20, sin),      # 80 パラメータ
    layer_2 = Dense(20 => 20, sin),     # 420 パラメータ
    layer_3 = Dense(20 => 20, sin),     # 420 パラメータ
    layer_4 = Dense(20 => 1),           # 21 パラメータ
)         # 合計: 941 パラメータ,
          #        0 ステート, サマリーサイズ 64 バイト.

# 入力層のために独自の初期化アルゴリズムを使用します。
julia> init_weight(rng::AbstractRNG, out_dims::Int, in_dims::Int) = randn(rng, Float32, out_dims, in_dims) .* 2.5f0
julia> chain = Siren(2, 1; num_layers = 4, hidden_dims = 50, init_weight = init_weight)
```

## 参考文献

[sitzmann2020implicit](@cite)
