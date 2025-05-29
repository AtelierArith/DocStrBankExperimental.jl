```
RCropRatio <: Augmentor.ImageOperation
```

## Description

Crops out the biggest possible area at some random position of the given image, such that the output image satisfies the specified aspect ratio (i.e. width divided by height).

For example the operation `RCropRatio(1)` would denote a crop for the biggest possible square. If there is more than one such square, then one will be selected at random.

## Usage

```
RCropRatio(ratio)

RCropRatio(; ratio = 1)
```

## Arguments

  * **`ratio::Number`** : Optional. A number denoting the aspect   ratio. For example specifying `ratio=16/9` would denote a 16:9   aspect ratio. Defaults to `1`, which describes a square crop.

## See also

[`RCropSize`](@ref), [`CropRatio`](@ref), [`CropSize`](@ref), [`Crop`](@ref), [`CropNative`](@ref), [`augment`](@ref)

## Examples

```julia
using Augmentor
img = testpattern()

# crop a randomly placed square of maxmimum size
augment(img, RCropRatio(1))
```
