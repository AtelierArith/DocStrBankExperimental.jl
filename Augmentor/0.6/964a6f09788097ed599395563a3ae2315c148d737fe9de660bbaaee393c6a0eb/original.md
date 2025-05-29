```
Resize <: Augmentor.ImageOperation
```

## Description

Rescales the image to a fixed pre-specified pixel size.

This operation does not take any measures to preserve aspect ratio of the source image. Instead, the original image will simply be resized to the given dimensions. This is useful when one needs a set of images to all be of the exact same size.

## Usage

```
Resize(; height=64, width=64)

Resize(size)

Resize(size...)
```

## Arguments

  * **`size`** : `NTuple` or `Vararg` of `Int` that denote the   output size in pixel for each dimension.

## See also

[`CropSize`](@ref), [`augment`](@ref)

## Examples

```julia
using Augmentor
img = testpattern()

augment(img, Resize(30, 40))
```
