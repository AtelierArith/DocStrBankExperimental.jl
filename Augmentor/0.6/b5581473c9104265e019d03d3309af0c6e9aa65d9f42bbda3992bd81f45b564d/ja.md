```
CropSize <: Augmentor.ImageOperation
```

## 説明

入力画像の中心周辺に指定されたピクセルサイズの領域を切り取ります。

例えば、操作 `CropSize(10, 50)` は、入力画像の中心周辺に高さ10、幅50の長方形を切り取ることを示します。

## 使用法

```
CropSize(size)

CropSize(size...)
```

## 引数

  * **`size`** : 各次元の出力サイズをピクセル単位で示す `NTuple` または `Int` の `Vararg`。

## 参照

[`CropRatio`](@ref), [`Crop`](@ref), [`CropNative`](@ref), [`augment`](@ref)

## 例

```julia
using Augmentor
img = testpattern()

# 回転した画像の中心周辺を切り取る
augment(img, Rotate(45) |> CropSize(300, 400))
```
