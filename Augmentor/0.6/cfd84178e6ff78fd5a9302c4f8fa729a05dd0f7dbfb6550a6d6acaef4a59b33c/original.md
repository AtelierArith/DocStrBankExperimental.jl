```
AggregateThenMapFun <: Augmentor.Operation
```

## Description

Compute some aggregated value of the current image using the given function `aggfun`, and map that value over the current image using the given function `mapfun`.

This is particularly useful for achieving effects such as per-image normalization.

## Usage

```
AggregateThenMapFun(aggfun, mapfun)
```

## Arguments

  * **`aggfun`** : A function that takes the whole current image as   input and which result will also be passed to `mapfun`. It   should have a signature of `img -> agg`, where `img` will the   the current image. What type and value `agg` should be is up   to the user.
  * **`mapfun`** : The binary function that should be mapped over   all individual array elements. It should have a signature of   `(px, agg) -> new_px` where `px` is a single element of the   current image, and `agg` is the output of `aggfun`.

## See also

[`MapFun`](@ref), [`ConvertEltype`](@ref), [`augment`](@ref)

## Examples

```julia
using Augmentor
img = testpattern()

# subtract the average RGB value of the current image
augment(img, AggregateThenMapFun(img -> mean(img), (px, agg) -> px - agg))
```
