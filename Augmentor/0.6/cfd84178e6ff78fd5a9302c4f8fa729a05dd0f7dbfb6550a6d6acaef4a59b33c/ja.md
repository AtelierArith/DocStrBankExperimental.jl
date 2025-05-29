```
AggregateThenMapFun <: Augmentor.Operation
```

## 説明

与えられた関数 `aggfun` を使用して現在の画像の集約値を計算し、その値を与えられた関数 `mapfun` を使用して現在の画像にマッピングします。

これは、画像ごとの正規化などの効果を達成するのに特に便利です。

## 使用法

```
AggregateThenMapFun(aggfun, mapfun)
```

## 引数

  * **`aggfun`** : 現在の画像全体を入力として受け取り、その結果が `mapfun` に渡される関数です。`img -> agg` のシグネチャを持つ必要があり、`img` は現在の画像になります。`agg` の型と値はユーザーに依存します。
  * **`mapfun`** : すべての個々の配列要素にマッピングされるべき二項関数です。`(px, agg) -> new_px` のシグネチャを持つ必要があり、`px` は現在の画像の単一要素で、`agg` は `aggfun` の出力です。

## 参照

[`MapFun`](@ref), [`ConvertEltype`](@ref), [`augment`](@ref)

## 例

```julia
using Augmentor
img = testpattern()

# 現在の画像の平均RGB値を引く
augment(img, AggregateThenMapFun(img -> mean(img), (px, agg) -> px - agg))
```
