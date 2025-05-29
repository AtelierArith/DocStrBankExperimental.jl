```
RCropRatio <: Augmentor.ImageOperation
```

## 説明

指定された画像の任意の位置で、出力画像が指定されたアスペクト比（すなわち、幅を高さで割った値）を満たすように、可能な限り大きな領域を切り取ります。

例えば、操作 `RCropRatio(1)` は、可能な限り大きな正方形の切り取りを示します。もしそのような正方形が複数ある場合は、その中からランダムに選択されます。

## 使用法

```
RCropRatio(ratio)

RCropRatio(; ratio = 1)
```

## 引数

  * **`ratio::Number`** : オプション。アスペクト比を示す数値です。例えば `ratio=16/9` を指定すると、16:9 のアスペクト比を示します。デフォルトは `1` で、正方形の切り取りを示します。

## 参照

[`RCropSize`](@ref), [`CropRatio`](@ref), [`CropSize`](@ref), [`Crop`](@ref), [`CropNative`](@ref), [`augment`](@ref)

## 例

```julia
using Augmentor
img = testpattern()

# 最大サイズのランダムに配置された正方形を切り取る
augment(img, RCropRatio(1))
```
