```
Rotate180 <: Augmentor.AffineOperation
```

## Description

Rotates the image 180 degrees. This is a special case rotation because it can be performed very efficiently by simply rearranging the existing pixels. Furthermore, the output image will have the same dimensions as the input image.

If created using the parameter `p`, the operation will be lifted into `Either(p=>Rotate180(), 1-p=>NoOp())`, where `p` denotes the probability of applying `Rotate180` and `1-p` the probability for applying [`NoOp`](@ref). See the documentation of [`Either`](@ref) for more information.

## Usage

```
Rotate180()

Rotate180(p)
```

## Arguments

  * **`p::Number`** : Optional. Probability of applying the   operation. Must be in the interval [0,1].

## See also

[`Rotate90`](@ref), [`Rotate270`](@ref), [`Rotate`](@ref), [`Either`](@ref), [`augment`](@ref)

## Examples

```jldoctest
julia> using Augmentor

julia> img = [200 150; 50 1]
2×2 Matrix{Int64}:
 200  150
  50    1

julia> img_new = augment(img, Rotate180())
2×2 Matrix{Int64}:
   1   50
 150  200
```
