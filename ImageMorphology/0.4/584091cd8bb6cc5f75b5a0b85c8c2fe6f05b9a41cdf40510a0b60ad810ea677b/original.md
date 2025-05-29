```
mgradient(img; mode=:beucher, dims=coords_spatial(img), r=1)
mgradient(img, se; mode=:beucher)
```

Calculate morphological gradient of the image using given mode.

There are three widely used modes[1]:

  * `:beucher`: the default mode. It calculates the arithmetic difference between the dilation and the erosion – `dilate(img, se) - erode(img, se)`.
  * `:internal`: also known as *half-gradient by erosion*. It calculates the arithmetic difference between the original image and its erosion – `img - erode(img, se)`.
  * `:external`: also known as *half-gradient by dilation*. It calculates the arithmetic difference between dilation and the original image – `dilate(img, se) - se`.

`se` is the structuring element that defines the neighborhood of the image. See [`strel`](@ref) for more details. If `se` is not specified, then it will use the [`strel_box`](@ref) with an extra keyword `dims` to control the dimensions to filter, and half-size `r` to control the diamond size.

# Examples

```jldoctest; setup = :(using ImageMorphology)
julia> img = falses(7, 7); img[3:5, 3:5] .= true; img
7×7 BitMatrix:
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  1  1  1  0  0
 0  0  1  1  1  0  0
 0  0  1  1  1  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0

julia> Int.(mgradient(img)) # default mode :beucher always creates a two-pixel wide boundary
7×7 Matrix{Int64}:
 0  0  0  0  0  0  0
 0  1  1  1  1  1  0
 0  1  1  1  1  1  0
 0  1  1  0  1  1  0
 0  1  1  1  1  1  0
 0  1  1  1  1  1  0
 0  0  0  0  0  0  0

julia> Int.(mgradient(img; mode=:internal)) # half-gradient -- the boundary is internal to original image
7×7 Matrix{Int64}:
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  1  1  1  0  0
 0  0  1  0  1  0  0
 0  0  1  1  1  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0

julia> Int.(mgradient(img; mode=:external)) # half-gradient -- the boundary is external to original image
7×7 Matrix{Int64}:
 0  0  0  0  0  0  0
 0  1  1  1  1  1  0
 0  1  0  0  0  1  0
 0  1  0  0  0  1  0
 0  1  0  0  0  1  0
 0  1  1  1  1  1  0
 0  0  0  0  0  0  0

julia> Int.(mgradient(img, strel_diamond(img))) # use diamond shape SE
7×7 Matrix{Int64}:
 0  0  0  0  0  0  0
 0  0  1  1  1  0  0
 0  1  1  1  1  1  0
 0  1  1  0  1  1  0
 0  1  1  1  1  1  0
 0  0  1  1  1  0  0
 0  0  0  0  0  0  0
```

The beucher operator is a self-complementary operator in the sense that `mgradient(img, se; mode=:beucher) == mgradient(complement.(img), se; mode=:beucher)`. When `r>1`, it is usually called *thick gradient*. If a line segment is used as `se`, then the gradient becomes the *directional gradient*.

## See also

  * [`mgradient!`](@ref) is the in-place version of this function.
  * [`mlaplacian`](@ref) for the laplacian operator.
  * `ImageBase.FiniteDiff` also provides a few finite difference operators, including `fdiff`, `fgradient`, etc.

## References

  * [1] Rivest, Jean-Francois, Pierre Soille, and Serge Beucher. "Morphological gradients." Journal of Electronic Imaging 2.4 (1993): 326-336.
