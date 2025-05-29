```
ShearY <: Augmentor.AffineOperation
```

## Description

Shear the image vertically for the given `degree`. This operation can only be performed as an affine transformation and will in general cause other operations of the pipeline to use their affine formulation as well (if they have one).

It will always perform the transformation around the center of the image. This can be particularly useful when combining the operation with [`CropNative`](@ref).

## Usage

```
ShearY(degree)
```

## Arguments

  * **`degree`** : `Real` or `AbstractVector` of `Real` that denote   the shearing angle(s) in degree. If a vector is provided,   then a random element will be sampled each time the operation   is applied.

## See also

[`ShearX`](@ref), [`CropNative`](@ref), [`augment`](@ref)

## Examples

```julia
using Augmentor
img = testpattern()

# shear vertically exactly 5 degree
augment(img, ShearY(5))

# shear vertically between 10 and 20 degree upwards
augment(img, ShearY(10:20))

# shear vertically one of the five specified degrees
augment(img, ShearY([-10, -5, 0, 5, 10]))
```
