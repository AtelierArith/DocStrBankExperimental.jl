```
RCropSize <: Augmentor.ImageOperation
```

## 説明

指定された画像のランダムな位置に、あらかじめ定義されたサイズの領域を切り取ります。

例えば、操作 `RCropSize(128, 64)` は、高さ128、幅64のランダムな切り取りを示します。`RCropSize(64)` は、サイズ64の正方形の切り取りを示します。

## 使用法

```
RCropSize(height, width)

RCropSize(width)
```

## 引数

  * **`height::Number`** : 切り取られた領域の高さ
  * **`width::Number`** : 切り取られた領域の幅

## 参照

[`RCropRatio`](@ref), [`CropRatio`](@ref), [`CropSize`](@ref), [`Crop`](@ref), [`CropNative`](@ref), [`augment`](@ref)

## 例

```julia
using Augmentor
img = testpattern()

# サイズ100のランダムに配置された正方形を切り取る
augment(img, RCropSize(100))
```
