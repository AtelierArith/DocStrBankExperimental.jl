```
CropRatio <: Augmentor.ImageOperation
```

## 説明

与えられた画像の中心周辺で、指定されたアスペクト比（すなわち、幅を高さで割った値）を満たすように、最大の領域を切り取ります。

例えば、`CropRatio(1)`という操作は、画像の中心周辺で最大の正方形を切り取ることを示します。

ランダムに配置された切り取りについては、[`RCropRatio`](@ref)を参照してください。

## 使用法

```
CropRatio(ratio)

CropRatio(; ratio = 1)
```

## 引数

  * **`ratio::Number`** : オプション。アスペクト比を示す数値。例えば、`ratio=16/9`を指定すると、16:9のアスペクト比を示します。デフォルトは`1`で、正方形の切り取りを示します。

## 参照

[`RCropRatio`](@ref), [`CropSize`](@ref), [`Crop`](@ref), [`CropNative`](@ref), [`augment`](@ref)

## 例

```julia
using Augmentor
img = testpattern()

# 画像の中心周辺で最大の正方形を切り取る
augment(img, CropRatio(1))
```
