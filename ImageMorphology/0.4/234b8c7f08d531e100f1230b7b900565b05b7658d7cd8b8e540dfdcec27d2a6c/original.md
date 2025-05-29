```
bothat(img; dims=coords_spatial(img), r=1)
bothat(img, se)
```

Performs morphological bottom-hat transform for given image, i.e., `closing(img, se) - img`.

`se` is the structuring element that defines the neighborhood of the image. See [`strel`](@ref) for more details. If `se` is not specified, then it will use the [`strel_box`](@ref) with an extra keyword `dims` to control the dimensions to filter, and half-size `r` to control the diamond size.

This bottom-hat transform, also known as *black* top-hat transform, can be used to extract small black elements and details from an image. To extract white details, the *white* top-hat transform [`tophat`](@ref) can be used.

# Examples

```jldoctest; setup = :(using ImageMorphology)
julia> img = falses(7, 7); img[3:5, 3:5] .= true; img[4, 6] = true; img[4, 4] = false; img
7×7 BitMatrix:
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  1  1  1  0  0
 0  0  1  0  1  1  0
 0  0  1  1  1  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0

julia> Int.(bothat(img))
7×7 Matrix{Int64}:
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  0  1  0  0  1
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0

julia> Int.(bothat(img, strel_diamond(img))) # use diamond shape SE
7×7 Matrix{Int64}:
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  0  1  0  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
```

See also [`bothat!`](@ref) for the in-place version.
