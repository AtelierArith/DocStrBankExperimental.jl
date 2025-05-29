```
MapFun <: Augmentor.Operation
```

## 説明

指定された関数をすべての個々の配列要素に適用します。

これは、指定された関数が個々の要素で呼び出され、元の要素の場所を取るべき変換された要素を返すことが期待されることを意味します。これはさらに、関数が単項であることが期待されることを示唆しています。関数はその戻り値の型と型安定性に一貫性があることが推奨されます。

## 使用法

```
MapFun(fun)
```

## 引数

  * **`fun`** : すべての個々の配列要素に適用されるべき単項関数。

## 参照

[`AggregateThenMapFun`](@ref), [`ConvertEltype`](@ref), [`augment`](@ref)

## 例

```julia
using Augmentor, ColorTypes
img = testpattern()

# 各ピクセルから定数RGBA値を引く
augment(img, MapFun(px -> px - RGBA(0.5, 0.3, 0.7, 0.0)))

# チャンネルを分離して各数値要素を定数値でスケーリング
pl = SplitChannels() |> MapFun(el -> el * 0.5) |> CombineChannels(RGBA)
augment(img, pl)
```
