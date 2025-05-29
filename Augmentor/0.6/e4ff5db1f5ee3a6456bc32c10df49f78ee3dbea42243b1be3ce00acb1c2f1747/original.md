```
FlipX <: Augmentor.AffineOperation
```

## Description

Reverses the x-order of each pixel row. Another way of describing it would be that it mirrors the image on the y-axis, or that it mirrors the image horizontally.

If created using the parameter `p`, the operation will be lifted into `Either(p=>FlipX(), 1-p=>NoOp())`, where `p` denotes the probability of applying `FlipX` and `1-p` the probability for applying [`NoOp`](@ref). See the documentation of [`Either`](@ref) for more information.

## Usage

```
FlipX()

FlipX(p)
```

## Arguments

  * **`p::Number`** : Optional. Probability of applying the   operation. Must be in the interval [0,1].

## See also

[`FlipY`](@ref), [`Either`](@ref), [`augment`](@ref)

## Examples

```jldoctest
julia> using Augmentor

julia> img = [200 150; 50 1]
2×2 Matrix{Int64}:
 200  150
  50    1

julia> img_new = augment(img, FlipX())
2×2 Matrix{Int64}:
 150  200
   1   50
```
