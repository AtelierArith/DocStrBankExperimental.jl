```
dilate(img; dims=coords_spatial(img), r=1)
dilate(img, se)
```

Perform a max-filter over the neighborhood of `img`, specified by structuring element `se`.

`se` is the structuring element that defines the neighborhood of the image. See [`strel`](@ref) for more details. If `se` is not specified, then it will use the [`strel_box`](@ref) with an extra keyword `dims` to control the dimensions to filter, and half-size `r` to control the diamond size.

# Examples

```jldoctest; setup = :(using ImageMorphology)
julia> img = falses(5, 5); img[3, [2, 4]] .= true; img
5×5 BitMatrix:
 0  0  0  0  0
 0  0  0  0  0
 0  1  0  1  0
 0  0  0  0  0
 0  0  0  0  0

julia> dilate(img)
5×5 BitMatrix:
 0  0  0  0  0
 1  1  1  1  1
 1  1  1  1  1
 1  1  1  1  1
 0  0  0  0  0

julia> dilate(img; dims=1)
5×5 BitMatrix:
 0  0  0  0  0
 0  1  0  1  0
 0  1  0  1  0
 0  1  0  1  0
 0  0  0  0  0

julia> dilate(img, strel_diamond(img)) # use diamond shape SE
5×5 BitMatrix:
 0  0  0  0  0
 0  1  0  1  0
 1  1  1  1  1
 0  1  0  1  0
 0  0  0  0  0
```

## See also

  * [`dilate!`](@ref) is the in-place version of this function
  * [`erode`](@ref) is the dual operator of `dilate` in the sense that `complement.(dilate(img)) == erode(complement.(img))`.

!!! note "symmetricity"
    If `se` is symmetric with repsect to origin, i.e., `se[b] == se[-b]` for any `b`, then dilation becomes the Minkowski sum: A⊕B={a+b|a∈A, b∈B}.

