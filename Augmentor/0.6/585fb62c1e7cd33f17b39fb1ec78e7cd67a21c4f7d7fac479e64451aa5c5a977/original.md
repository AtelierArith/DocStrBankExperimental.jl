```
CropNative <: Augmentor.ImageOperation
```

## Description

Crops out the area denoted by the specified pixel ranges.

For example the operation `CropNative(5:100, 2:10)` would denote a crop for the rectangle that starts at `x=2` and `y=5` in the top left corner of native space and ends at `x=10` and `y=100` in the bottom right corner of native space.

In contrast to [`Crop`](@ref), the position `x=1` `y=1` is not necessarily located at the top left of the current image, but instead depends on the cumulative effect of the previous transformations. The reason for this is because affine transformations are usually performed around the center of the image, which is reflected in "native space". This is useful for combining transformations such as [`Rotate`](@ref) or [`ShearX`](@ref) with a crop around the center area.

## Usage

```
CropNative(indices)

CropNative(indices...)
```

## Arguments

  * **`indices`** : `NTuple` or `Vararg` of `UnitRange` that denote   the cropping range for each array dimension. This is very   similar to how the axes for `view` are specified.

## See also

[`Crop`](@ref), [`CropSize`](@ref), [`CropRatio`](@ref), [`augment`](@ref)

## Examples

```julia
using Augmentor
img = testpattern()

# cropped at top left corner
augment(img, Rotate(45) |> Crop(1:300, 1:400))

# cropped around center of rotated image
augment(img, Rotate(45) |> CropNative(1:300, 1:400))
```
