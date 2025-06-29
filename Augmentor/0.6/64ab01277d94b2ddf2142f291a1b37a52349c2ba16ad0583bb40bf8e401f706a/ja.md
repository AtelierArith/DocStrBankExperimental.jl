```
Scale <: Augmentor.AffineOperation
```

## 説明

指定された `factors` によって画像の高さと幅を乗算します。これは、出力画像のサイズが入力画像のサイズに依存することを意味します。

提供された `factors` は、数値または数値のベクトルのいずれかである可能性があります。

  * 数値が提供される場合、操作は決定論的であり、常に同じ因子で入力画像をスケーリングします。
  * ベクトルが提供される場合、操作が適用されるたびに有効なインデックスがサンプリングされ、そのインデックスに対応する要素がスケーリング因子として使用されます。

スケーリングは画像の中心に対して行われ、これは [`CropNative`](@ref) で操作を続ける際に便利です。

## 使用法

```
Scale(factors)

Scale(factors...)
```

## 引数

  * **`factors`** : 各配列次元のスケール因子を示す `NTuple` または `Vararg` の `Real` または `AbstractVector`。1つの変数のみが指定された場合、高さと幅は同じ因子でスケーリングされると見なされます。

## 参照

[`Zoom`](@ref), [`Resize`](@ref), [`augment`](@ref)

## 例

```julia
using Augmentor
img = testpattern()

# 画像サイズを半分にする
augment(img, Scale(0.5))

# 1.2、1.3、または1.4のランダムな因子で均等にスケーリング
augment(img, Scale([1.2, 1.3, 1.4]))

# 0.5x0.7または0.6x0.8でスケーリング
augment(img, Scale([0.5, 0.6], [0.7, 0.8]))
```
