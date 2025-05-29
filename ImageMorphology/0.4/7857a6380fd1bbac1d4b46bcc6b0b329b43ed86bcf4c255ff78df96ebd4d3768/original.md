```
tophat(img; dims=coords_spatial(img), r=1)
tophat(img, se)
```

Performs morphological top-hat transform for given image, i.e., `img - opening(img, se)`.

`se` is the structuring element that defines the neighborhood of the image. See [`strel`](@ref) for more details. If `se` is not specified, then it will use the [`strel_box`](@ref) with an extra keyword `dims` to control the dimensions to filter, and half-size `r` to control the diamond size.

This *white* top-hat transform can be used to extract small white elements and details from an image. To extract black details, the *black* top-hat transform, also known as bottom-hat transform, [`bothat`](@ref) can be used.

# Examples

```jldoctest; setup = :(using ImageMorphology)
julia> img = falses(5, 5); img[1, 1] = true; img[3:5, 3:5] .= true; img
5×5 BitMatrix:
 1  0  0  0  0
 0  0  0  0  0
 0  0  1  1  1
 0  0  1  1  1
 0  0  1  1  1

julia> Int.(tophat(img))
5×5 Matrix{Int64}:
 1  0  0  0  0
 0  0  0  0  0
 0  0  0  0  0
 0  0  0  0  0
 0  0  0  0  0

julia> Int.(tophat(img, strel_diamond(img))) # use diamond shape SE
5×5 Matrix{Int64}:
 1  0  0  0  0
 0  0  0  0  0
 0  0  1  0  0
 0  0  0  0  0
 0  0  0  0  0
```
