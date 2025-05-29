```
Chain(layers...; name=nothing)
Chain(; layers..., name=nothing)
```

複数のレイヤー/関数を収集し、与えられた入力に対して順次呼び出します。

## 引数

  * レイヤーは2つの形式で指定できます：

      * `N`個のLuxレイヤーのリスト
      * `N`個のキーワード引数として指定。

# 拡張ヘルプ

## 入力

入力`x`は各レイヤーに順次渡され、内部レイヤーの入力要件に適合する必要があります。

## 戻り値

  * `x`にすべてのレイヤーを順次適用した後の出力
  * 更新されたモデルの状態

## パラメータ

  * 各`layer`のパラメータは、`fields = layer_1, layer_2, ..., layer_N`を持つNamedTupleでラップされます（kwargs APIを使用する場合、名前は変更されます）。

## 状態

  * 各`layer`の状態は、`fields = layer_1, layer_2, ..., layer_N`を持つNamedTupleでラップされます（kwargs APIを使用する場合、名前は変更されます）。

## その他のプロパティ

  * インデックスおよびフィールドアクセス構文を許可します。`m[i]`または`m.layer_i`を使用して`i`番目のレイヤーにアクセスできます。また、範囲や配列を使用してインデックスを付けることもできます。

## 例

```jldoctest
julia> Chain(Dense(2, 3, relu), BatchNorm(3), Dense(3, 2))
Chain(
    layer_1 = Dense(2 => 3, relu),      # 9パラメータ
    layer_2 = BatchNorm(3, affine=true, track_stats=true),  # 6パラメータ、さらに7
    layer_3 = Dense(3 => 2),            # 8パラメータ
)         # 合計: 23パラメータ、
          #        さらに7状態。

julia> Chain(Dense(2, 3, relu), BatchNorm(3), Dense(3, 2); name="MyFancyChain")
MyFancyChain(
    layer_1 = Dense(2 => 3, relu),      # 9パラメータ
    layer_2 = BatchNorm(3, affine=true, track_stats=true),  # 6パラメータ、さらに7
    layer_3 = Dense(3 => 2),            # 8パラメータ
)         # 合計: 23パラメータ、
          #        さらに7状態。
```
