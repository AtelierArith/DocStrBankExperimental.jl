```
hmaxima(img, h; [dims])
hmaxima(img, h; se)
```

Compute regional maxima of height h.

For grayscale image `img`, the hmaxima transformation suppresses all regional maxima whose height is below a given threshold level `h`.

The `dims` keyword is used to specify the dimension to process by constructing the box shape structuring element [`strel_box(img; dims)`](@ref strel_box). For generic structuring element, the half-size is expected to be either `0` or `1` along each dimension.

# Examples

```jldoctest; setup=:(using ImageMorphology, ImageMorphology.FixedPointNumbers)
julia> img = UInt8[3 3 3 3 3 3 3 3 3 3; 3 4 4 4 3 3 4 4 4 3; 3 4 5 4 3 3 4 9 4 3; 3 4 4 4 3 3 4 4 4 3; 3 3 3 3 3 3 3 3 3 3]
5×10 Matrix{UInt8}:
 0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03
 0x03  0x04  0x04  0x04  0x03  0x03  0x04  0x04  0x04  0x03
 0x03  0x04  0x05  0x04  0x03  0x03  0x04  0x09  0x04  0x03
 0x03  0x04  0x04  0x04  0x03  0x03  0x04  0x04  0x04  0x03
 0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03

julia> out = hmaxima(reinterpret(N0f8, img), reinterpret(N0f8, UInt8(3)))
5×10 Array{N0f8,2} with eltype N0f8:
 0.012  0.012  0.012  0.012  0.012  0.012  0.012  0.012  0.012  0.012
 0.012  0.012  0.012  0.012  0.012  0.012  0.016  0.016  0.016  0.012
 0.012  0.012  0.012  0.012  0.012  0.012  0.016  0.024  0.016  0.012
 0.012  0.012  0.012  0.012  0.012  0.012  0.016  0.016  0.016  0.012
 0.012  0.012  0.012  0.012  0.012  0.012  0.012  0.012  0.012  0.012

julia> ref_img = UInt8[3 3 3 3 3 3 3 3 3 3; 3 3 3 3 3 3 4 4 4 3; 3 3 3 3 3 3 4 6 4 3; 3 3 3 3 3 3 4 4 4 3; 3 3 3 3 3 3 3 3 3 3]
5×10 Matrix{UInt8}:
 0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03
 0x03  0x03  0x03  0x03  0x03  0x03  0x04  0x04  0x04  0x03
 0x03  0x03  0x03  0x03  0x03  0x03  0x04  0x06  0x04  0x03
 0x03  0x03  0x03  0x03  0x03  0x03  0x04  0x04  0x04  0x03
 0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03  0x03

julia> eltype(out) == N0f8
true

julia> out == reinterpret(N0f8, ref_img)
true
```

# See also

The inplace version of this function is `hmaxima!`.

# References

  * [1] L. Vincent, “Morphological grayscale reconstruction in image analysis: applications and efficient algorithms,” IEEE Trans. on Image Process., vol. 2, no. 2, pp. 176–201, Apr. 1993, doi: 10.1109/83.217222.
  * [2] P. Soille, Morphological Image Analysis. Berlin, Heidelberg: Springer Berlin Heidelberg, 2004. doi: 10.1007/978-3-662-05088-0.
