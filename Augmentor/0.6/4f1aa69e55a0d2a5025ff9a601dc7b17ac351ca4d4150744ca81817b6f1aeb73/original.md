```
CropRatio <: Augmentor.ImageOperation
```

## Description

Crops out the biggest area around the center of the given image such that the output image satisfies the specified aspect ratio (i.e. width divided by height).

For example the operation `CropRatio(1)` would denote a crop for the biggest square around the center of the image.

For randomly placed crops take a look at [`RCropRatio`](@ref).

## Usage

```
CropRatio(ratio)

CropRatio(; ratio = 1)
```

## Arguments

  * **`ratio::Number`** : Optional. A number denoting the aspect   ratio. For example specifying `ratio=16/9` would denote a 16:9   aspect ratio. Defaults to `1`, which describes a square crop.

## See also

[`RCropRatio`](@ref), [`CropSize`](@ref), [`Crop`](@ref), [`CropNative`](@ref), [`augment`](@ref)

## Examples

```julia
using Augmentor
img = testpattern()

# crop biggest square around the image center
augment(img, CropRatio(1))
```
