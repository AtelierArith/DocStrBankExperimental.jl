```
jpeg_encode(filename::AbstractString, img; kwargs...) -> Int
jpeg_encode(io::IO, img; kwargs...) -> Int
jpeg_encode(img; kwargs...) -> Vector{UInt8}
```

Encode 2D image `img` as JPEG byte sequences and write to given I/O stream or file. The return value is number of bytes. If output is not specified, the encoded result is stored in memory as return value.

# Parameters

  * `transpose::Bool`: whether we need to permute the image's width and height dimension before encoding. The default value is `false`.
  * `quality::Int`: Constructs JPEG quantization tables appropriate for the indicated quality setting. The quality value is expressed on the 0..100 scale recommended by IJG. The default value is `92`. Pass `quality=nothing` to let libjpeg-turbo dynamicly guess a value.

!!! info "Custom compression parameters"
    JPEG has a large number of compression parameters that determine how the image is encoded. Most applications don't need or want to know about all these parameters. For more detailed information and explaination, please refer to the "Compression parameter selection" in [1]. Unsupported custom parameters might cause Julia segmentation fault.


# Examples

```jldoctest
julia> using JpegTurbo, TestImages

julia> img = testimage("cameraman");

julia> jpeg_encode("out.jpg", img) # write to file
51396

julia> buf = jpeg_encode(img); length(buf) # directly write to memory
51396
```

# References

  * [1] [libjpeg API Documentation (libjpeg.txt)](https://raw.githubusercontent.com/libjpeg-turbo/libjpeg-turbo/main/libjpeg.txt)
