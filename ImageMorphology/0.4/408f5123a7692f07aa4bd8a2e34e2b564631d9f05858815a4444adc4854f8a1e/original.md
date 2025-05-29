```
hminima(img, h; [dims])
hminima(img, h; se)
```

Compute regional minima of depth h.

For grayscale image `img`, the hminima transformation suppresses all regional minima whose depth is below a given threshold level `h`.

The `dims` keyword is used to specify the dimension to process by constructing the box shape structuring element [`strel_box(img; dims)`](@ref strel_box). For generic structuring element, the half-size is expected to be either `0` or `1` along each dimension.

# Examples

```jldoctest; setup=:(using ImageMorphology, ImageMorphology.FixedPointNumbers) julia> img = UInt8[8 8 8 8 8 8 8 8 8 8; 8 7 7 7 8 8 7 7 7 8; 8 7 6 7 8 8 7 3 7 8; 8 7 7 7 8 8 7 7 7 8; 8 8 8 8 8 8 8 8 8 8] 5×10 Matrix{UInt8}:  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x07  0x07  0x07  0x08  0x08  0x07  0x07  0x07  0x08  0x08  0x07  0x06  0x07  0x08  0x08  0x07  0x03  0x07  0x08  0x08  0x07  0x07  0x07  0x08  0x08  0x07  0x07  0x07  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08

julia> out = hminima(reinterpret(N0f8, img), reinterpret(N0f8, UInt8(3))) 5×10 Array{N0f8,2} with eltype N0f8:  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.027  0.027  0.027  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.027  0.024  0.027  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.027  0.027  0.027  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031  0.031

julia> ref_img = UInt8[8 8 8 8 8 8 8 8 8 8; 8 8 8 8 8 8 7 7 7 8; 8 8 8 8 8 8 7 6 7 8; 8 8 8 8 8 8 7 7 7 8; 8 8 8 8 8 8 8 8 8 8] 5×10 Matrix{UInt8}:  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x07  0x07  0x07  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x07  0x06  0x07  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x07  0x07  0x07  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08  0x08

julia> eltype(out) == N0f8 true

julia> out == reinterpret(N0f8, ref_img) true

# See also

The inplace version of this function is `hminima!`.

# References

  * [1] L. Vincent, “Morphological grayscale reconstruction in image analysis: applications and efficient algorithms,” IEEE Trans. on Image Process., vol. 2, no. 2, pp. 176–201, Apr. 1993, doi: 10.1109/83.217222.
  * [2] P. Soille, Morphological Image Analysis. Berlin, Heidelberg: Springer Berlin Heidelberg, 2004. doi: 10.1007/978-3-662-05088-0.
