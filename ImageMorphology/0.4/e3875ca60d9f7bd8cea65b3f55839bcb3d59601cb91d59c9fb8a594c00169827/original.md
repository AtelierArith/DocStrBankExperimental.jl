```
opening(img; dims=coords_spatial(img), r=1)
opening(img, se)
```

Perform the morphological opening on `img`. The opening operation is defined as erosion followed by a dilation: `dilate(erode(img, se), se)`.

`se` is the structuring element that defines the neighborhood of the image. See [`strel`](@ref) for more details. If `se` is not specified, then it will use the [`strel_box`](@ref) with an extra keyword `dims` to control the dimensions to filter, and half-size `r` to control the diamond size.

# Examples

```jldoctest; setup = :(using ImageMorphology)
julia> img = trues(7,7); img[2, 2] = false; img[3:5, 3:5] .= false; img[4, 4] = true; img
7×7 BitMatrix:
 1  1  1  1  1  1  1
 1  0  1  1  1  1  1
 1  1  0  0  0  1  1
 1  1  0  1  0  1  1
 1  1  0  0  0  1  1
 1  1  1  1  1  1  1
 1  1  1  1  1  1  1

julia> opening(img)
7×7 BitMatrix:
 0  0  1  1  1  1  1
 0  0  1  1  1  1  1
 1  1  0  0  0  1  1
 1  1  0  0  0  1  1
 1  1  0  0  0  1  1
 1  1  1  1  1  1  1
 1  1  1  1  1  1  1

julia> opening(img, strel_diamond(img)) # use diamond shape SE
7×7 BitMatrix:
 1  1  1  1  1  1  1
 1  0  1  1  1  1  1
 1  1  0  0  0  1  1
 1  1  0  0  0  1  1
 1  1  0  0  0  1  1
 1  1  1  1  1  1  1
 1  1  1  1  1  1  1
```

## See also

  * [`opening!`](@ref) is the in-place version of this function.
  * [`closing`](@ref) is the dual operator of `opening` in the sense that `complement.(opening(img)) == closing(complement.(img))`.
