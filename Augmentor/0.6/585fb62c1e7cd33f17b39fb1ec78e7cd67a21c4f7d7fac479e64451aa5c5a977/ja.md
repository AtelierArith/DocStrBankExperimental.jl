```
CropNative <: Augmentor.ImageOperation
```

## 説明

指定されたピクセル範囲によって示される領域を切り取ります。

例えば、操作 `CropNative(5:100, 2:10)` は、ネイティブ空間の左上隅で `x=2` と `y=5` から始まり、ネイティブ空間の右下隅で `x=10` と `y=100` で終わる矩形の切り取りを示します。

[`Crop`](@ref) と対照的に、位置 `x=1` `y=1` は現在の画像の左上隅に必ずしも位置するわけではなく、代わりに前の変換の累積効果に依存します。これは、アフィン変換が通常画像の中心を基準に行われるためであり、これは「ネイティブ空間」に反映されています。これは、中心領域の周りでの切り取りと [`Rotate`](@ref) や [`ShearX`](@ref) のような変換を組み合わせるのに便利です。

## 使用法

```
CropNative(indices)

CropNative(indices...)
```

## 引数

  * **`indices`** : 各配列次元の切り取り範囲を示す `UnitRange` の `NTuple` または `Vararg`。これは `view` の軸が指定される方法に非常に似ています。

## 参照

[`Crop`](@ref), [`CropSize`](@ref), [`CropRatio`](@ref), [`augment`](@ref)

## 例

```julia
using Augmentor
img = testpattern()

# 左上隅で切り取る
augment(img, Rotate(45) |> Crop(1:300, 1:400))

# 回転した画像の中心周りで切り取る
augment(img, Rotate(45) |> CropNative(1:300, 1:400))
```
