```
FlipY <: Augmentor.AffineOperation
```

## Description

Reverses the y-order of each pixel column. Another way of describing it would be that it mirrors the image on the x-axis, or that it mirrors the image vertically.

If created using the parameter `p`, the operation will be lifted into `Either(p=>FlipY(), 1-p=>NoOp())`, where `p` denotes the probability of applying `FlipY` and `1-p` the probability for applying [`NoOp`](@ref). See the documentation of [`Either`](@ref) for more information.

## Usage

```
FlipY()

FlipY(p)
```

## Arguments

  * **`p::Number`** : Optional. Probability of applying the   operation. Must be in the interval [0,1].

## See also

[`FlipX`](@ref), [`Either`](@ref), [`augment`](@ref)

## Examples

```jldoctest
julia> using Augmentor

julia> img = [200 150; 50 1]
2×2 Matrix{Int64}:
 200  150
  50    1

julia> img_new = augment(img, FlipY())
2×2 Matrix{Int64}:
  50    1
 200  150
```
