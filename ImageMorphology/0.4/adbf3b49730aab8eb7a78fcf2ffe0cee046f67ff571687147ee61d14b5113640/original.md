```
mreconstruct(op, marker, mask; [dims])
mreconstruct(op, marker, mask, se)
```

Morphological reconstruction of `marker` image by operation `op`.

The `op` argument is either `erode` or `dilate`, indicating reconstruction by erosion or by dilation. The `mask` argument has the same shape as `marker` and is used to restrict the output value range.

The `dims` keyword is used to specify the dimension to process by constructing the box shape structuring element [`strel_box(marker; dims)`](@ref strel_box). For generic structuring element, the half-size is expected to be either `0` or `1` along each dimension.

By definition, the reconstruction is done by applying `marker = select.(op(marker; dims), mask)` repeatly until reaching stability. For dilation `op, select = dilate, min` and for erosion `op, select = erode, max`.

# Examples

```jldoctest; setup=:(using ImageMorphology)
julia> marker = [0 0 0 0 0; 0 9 0 0 0; 0 0 0 0 0; 0 0 0 5 0; 0 0 0 0 0; 0 9 0 0 0]
6×5 Matrix{Int64}:
 0  0  0  0  0
 0  9  0  0  0
 0  0  0  0  0
 0  0  0  5  0
 0  0  0  0  0
 0  9  0  0  0

julia> mask = [9 0 0 0 0; 0 8 7 1 0; 0 9 0 4 0; 0 0 0 4 0; 0 0 6 5 6; 0 0 9 8 9]
6×5 Matrix{Int64}:
 9  0  0  0  0
 0  8  7  1  0
 0  9  0  4  0
 0  0  0  4  0
 0  0  6  5  6
 0  0  9  8  9

julia> mreconstruct(dilate, marker, mask) # equivalent to underbuild(marker, mask)
6×5 Matrix{Int64}:
 8  0  0  0  0
 0  8  7  1  0
 0  8  0  4  0
 0  0  0  4  0
 0  0  4  4  4
 0  0  4  4  4
```

# See also

The inplace version of this function is [`mreconstruct!`](@ref). There are also aliases [`underbuild`](@ref) for reconstruction by dilation and [`overbuild`](@ref) for reconstruction by erosion.

# References

  * [1] L. Vincent, “Morphological grayscale reconstruction in image analysis: applications and efficient algorithms,” IEEE Trans. on Image Process., vol. 2, no. 2, pp. 176–201, Apr. 1993, doi: 10.1109/83.217222.
  * [2] P. Soille, Morphological Image Analysis. Berlin, Heidelberg: Springer Berlin Heidelberg, 2004. doi: 10.1007/978-3-662-05088-0.
