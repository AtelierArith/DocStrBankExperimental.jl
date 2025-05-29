```
Rotate <: Augmentor.AffineOperation
```

## Description

Rotate the image upwards for the given `degree`. This operation can only be performed as an affine transformation and will in general cause other operations of the pipeline to use their affine formulation as well (if they have one).

In contrast to the special case rotations (e.g. [`Rotate90`](@ref), the type `Rotate` can describe any arbitrary number of degrees. It will always perform the rotation around the center of the image. This can be particularly useful when combining the operation with [`CropNative`](@ref).

## Usage

```
Rotate(degree)
```

## Arguments

  * **`degree`** : `Real` or `AbstractVector` of `Real` that denote   the rotation angle(s) in degree. If a vector is provided,   then a random element will be sampled each time the operation   is applied.

## See also

[`Rotate90`](@ref), [`Rotate180`](@ref), [`Rotate270`](@ref), [`CropNative`](@ref), [`augment`](@ref)

## Examples

```julia
using Augmentor
img = testpattern()

# rotate exactly 45 degree
augment(img, Rotate(45))

# rotate between 10 and 20 degree upwards
augment(img, Rotate(10:20))

# rotate one of the five specified degrees
augment(img, Rotate([-10, -5, 0, 5, 10]))
```
