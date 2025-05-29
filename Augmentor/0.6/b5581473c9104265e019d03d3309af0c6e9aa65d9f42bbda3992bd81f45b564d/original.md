```
CropSize <: Augmentor.ImageOperation
```

## Description

Crops out the area of the specified pixel size around the center of the input image.

For example the operation `CropSize(10, 50)` would denote a crop for a rectangle of height 10 and width 50 around the center of the input image.

## Usage

```
CropSize(size)

CropSize(size...)
```

## Arguments

  * **`size`** : `NTuple` or `Vararg` of `Int` that denote the   output size in pixel for each dimension.

## See also

[`CropRatio`](@ref), [`Crop`](@ref), [`CropNative`](@ref), [`augment`](@ref)

## Examples

```julia
using Augmentor
img = testpattern()

# cropped around center of rotated image
augment(img, Rotate(45) |> CropSize(300, 400))
```
