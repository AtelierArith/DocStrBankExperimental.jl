```
BranchLayer(layers...)
BranchLayer(; name=nothing, layers...)
```

入力 `x` を受け取り、すべての `layers` を通過させて出力のタプルを返します。

## 引数

  * レイヤーは2つの形式で指定できます：

      * `N` 個の Lux レイヤーのリスト
      * `N` のキーワード引数として指定。

# 拡張ヘルプ

## 入力

  * `x`: 各 `layers` に直接渡されます。

## 戻り値

  * タプル: `(layer_1(x), layer_2(x), ..., layer_N(x))`  （kwargs APIを使用する場合、名前が変更されます）
  * `layers` の更新された状態

## パラメータ

  * 各 `layer` のパラメータは、`fields = layer_1, layer_2, ..., layer_N` の NamedTuple にラップされています（kwargs APIを使用する場合、名前が変更されます）

## 状態

  * 各 `layer` の状態は、`fields = layer_1, layer_2, ..., layer_N` の NamedTuple にラップされています（kwargs APIを使用する場合、名前が変更されます）

!!! tip "Parallelとの比較"
    これは [`Parallel(nothing, layers...)`](@ref) とは少し異なります。

      * 入力がタプルの場合、`Parallel` は各要素を個別に各レイヤーに渡します。
      * `BranchLayer` は本質的に1つの入力があり、`N` の出力に分岐することを前提としています。


## 例

NTupleに入力を複製する簡単な方法は次のとおりです。

```jldoctest
julia> BranchLayer(NoOpLayer(), NoOpLayer(), NoOpLayer())
BranchLayer(
    layer_1 = NoOpLayer(),
    layer_2 = NoOpLayer(),
    layer_3 = NoOpLayer(),
)         # 合計: 0 パラメータ、
          #        さらに 0 状態。
```
