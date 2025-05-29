```
DeepONet(branch_net, trunk_net;
         flatten_layer=FlattenLayer(),
         linear_layer=NoOpLayer(),
         bias=ScalarLayer())
DeepONet(layer_sizes_branch, activation_branch,
         layer_sizes_trunk,
         activation_trunk,
         layer_sizes_linear=nothing)
```

深層演算子ネットワーク。ブランチネットは多次元入力をサポートしていることに注意してください。`flatten_layer`はブランチネットの出力を行列にフラット化し、`linear_layer`はフラット化された出力に適用されます。この場合、`linear_layer`はフラット化された行列を正しい形状に変換するために与えられなければなりません。

```
v → branch_net → flatten_layer → linear_layer → b
                                                  ↘
                                                    b' * t + bias → u
                                                  ↗
                                ξ → trunk_net → t
```

## 引数

  * `branch_net`: ブランチネット。
  * `trunk_net`: トランクネット。

## キーワード引数

  * `flatten_layer`: 多次元配列を行列にフラット化するためのレイヤー。
  * `linear_layer`: `flatten_layer`の出力に線形変換を適用するためのレイヤー。

## 入力

  * `(v, ξ)`: `v`は形状が$(b_1,b_2,...b_d, m)$の配列で、$R^d$から$R$への$m$関数の離散化です。$ξ$は形状が$(d', n)$の行列で、ドメイン$R^{d'}$の$n$データポイントを表します。

## 戻り値

  * 形状が$(m, n)$の行列。

## 例

```julia
julia> deeponet = DeepONet((3, 5, 4), relu, (2, 6, 4, 4), tanh)
DeepONet(
    branch_net = Chain(
        layer_1 = Dense(3 => 5, relu),  # 20パラメータ
        layer_2 = Dense(5 => 4),        # 24パラメータ
    ),
    trunk_net = Chain(
        layer_1 = Dense(2 => 6, tanh_fast),  # 18パラメータ
        layer_2 = Dense(6 => 4, tanh_fast),  # 28パラメータ
        layer_3 = Dense(4 => 4, tanh_fast),  # 20パラメータ
    ),
    flatten_layer = FlattenLayer(),
    linear_layer = NoOpLayer(),
    bias = ScalarLayer(),                    # 1パラメータ
)         # 合計: 111パラメータ,
          #        0状態、サマリーサイズ80バイト。
```

## 参考文献

[lu2019deeponet](@cite)
