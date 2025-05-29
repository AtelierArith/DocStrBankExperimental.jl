```
MapFun <: Augmentor.Operation
```

## Description

Maps the given function over all individual array elements.

This means that the given function is called with an individual elements and is expected to return a transformed element that should take the original's place. This further implies that the function is expected to be unary. It is encouraged that the function should be consistent with its return type and type-stable.

## Usage

```
MapFun(fun)
```

## Arguments

  * **`fun`** : The unary function that should be mapped over all   individual array elements.

## See also

[`AggregateThenMapFun`](@ref), [`ConvertEltype`](@ref), [`augment`](@ref)

## Examples

```julia
using Augmentor, ColorTypes
img = testpattern()

# subtract the constant RGBA value from each pixel
augment(img, MapFun(px -> px - RGBA(0.5, 0.3, 0.7, 0.0)))

# separate channels to scale each numeric element by a constant value
pl = SplitChannels() |> MapFun(el -> el * 0.5) |> CombineChannels(RGBA)
augment(img, pl)
```
