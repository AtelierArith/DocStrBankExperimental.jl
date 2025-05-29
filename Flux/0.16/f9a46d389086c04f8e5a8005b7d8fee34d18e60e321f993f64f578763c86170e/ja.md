```
@autosize (size...,) Chain(Layer(_ => 2), Layer(_), ...)
```

指定されたモデルを返し、各`_`は与えられた`size`の入力に対して推測された数に置き換えられます。

不明なサイズは通常、そのレイヤーの入力の第二から最後の次元であり、Fluxはこれをチャネル次元と見なします。（いくつかのレイヤー、`Dense` & [`LayerNorm`](@ref) は常に最初の次元を使用します。）アンダースコアはレイヤーの引数として現れることがあり、`=>`の内部でも使用されることがあります。`Dense(_ => _÷4)`のように、さらなる計算に使用されることもあります。

# 例

```
julia> @autosize (3, 1) Chain(Dense(_ => 2, sigmoid), BatchNorm(_, affine=false))
Chain(
  Dense(3 => 2, σ),                     # 8 パラメータ
  BatchNorm(2, affine=false),
) 

julia> img = [28, 28];

julia> @autosize (img..., 1, 32) Chain(              # サイズは実行時にのみ必要
          Chain(c = Conv((3,3), _ => 5; stride=2, pad=SamePad()),
                p = MeanPool((3,3)),
                b = BatchNorm(_),
                f = Flux.flatten),
          Dense(_ => _÷4, relu, init=Flux.rand32),   # 出力サイズ _÷4 を計算できる
          SkipConnection(Dense(_ => _, relu), +),
          Dense(_ => 10),
       )
Chain(
  Chain(
    c = Conv((3, 3), 1 => 5, pad=1, stride=2),  # 50 パラメータ
    p = MeanPool((3, 3)),
    b = BatchNorm(5),                   # 10 パラメータ、さらに10
    f = Flux.flatten,
  ),
  Dense(80 => 20, relu),                # 1_620 パラメータ
  SkipConnection(
    Dense(20 => 20, relu),              # 420 パラメータ
    +,
  ),
  Dense(20 => 10),                      # 210 パラメータ
)         # 合計: 10 の学習可能な配列、2_310 パラメータ、
          # さらに2つの非学習可能な、10 パラメータ、サマリーサイズ 10.469 KiB.

julia> outputsize(ans, (28, 28, 1, 32))
(10, 32)
```

制限事項:

  * `@autosize (5, 32) Flux.Bilinear(_ => 7)` は問題ありませんが、`Bilinear((_, _) => 7)` のようなものは失敗します。
  * `Scale(_)` と `LayerNorm(_)` は問題ありません（最初の次元を使用します）が、`Scale(_,_)` と `LayerNorm(_,_)` は `size(x,1) != size(x,2)` の場合に失敗します。
