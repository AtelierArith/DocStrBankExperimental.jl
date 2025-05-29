```
jpeg_decode([T,] filename::AbstractString; kwargs...) -> Matrix{T}
jpeg_decode([T,] io::IO; kwargs...) -> Matrix{T}
jpeg_decode([T,] data::Vector{UInt8}; kwargs...) -> Matrix{T}
```

Decode the JPEG image as colorant matrix. The source data can be either a filename, an IO , or an in-memory byte sequence.

# parameters

  * `transpose::Bool`: whether we need to permute the image's width and height dimension before encoding. The default value is `false`.
  * `scale_ratio::Real`: scale the image by ratio `scale_ratio` in `M/8` with `M ∈ 1:16`. The default value is `1`. For values are not in the range, they will be mapped to the nearest value, e.g., `0.3 => 2/8` and `0.35 => 3/8`. `scale_ratio` and `preferred_size` may not be used together.
  * `preferred_size::Tuple`: infer the minimal `scale_ratio` that `all(size(out) .>= preferred_size))` holds. It can optionally be `(op, preferred_size)` format, with compare operation `op` be one of `>`, `>=`, `<` or `<=`. If `op in (>=, >)` then it gets the minimal `scale_ratio`, otherwise it gets the maximum `scale_ratio` for `op in (<=, <)`. `scale_ratio` and `preferred_size` may not be used together. The `preferred_size` dimensions are not affected by keyword `transpose`.

# Examples

```jldoctest
julia> using JpegTurbo, TestImages, ImageCore

julia> filename = testimage("earth", download_only=true);

julia> img = jpeg_decode(filename); summary(img)
"3002×3000 Matrix{RGB{N0f8}}"

julia> img = jpeg_decode(Gray, filename; scale_ratio=0.25); summary(img)
"751×750 Matrix{Gray{N0f8}}"
```

For image preview and similar purposes, `T` and `scale_ratio` are useful parameters to accelerate the JPEG decoding process. For color JPEG image, `jpeg_decode(Gray, filename)` is faster than `jpeg_decode(filename)` since the color components need not be processed. Smaller `scale_ratio` permits significantly faster decoding since fewer pixels need be processed and a simpler IDCT method can be used.

```julia
using BenchmarkTools, TestImages, JpegTurbo
filename = testimage("earth", download_only=true)
# full decompression
@btime jpeg_decode(filename); # 224.760 ms (7 allocations: 51.54 MiB)
# only decompress luminance component
@btime jpeg_decode(Gray, filename); # 91.157 ms (6 allocations: 17.18 MiB)
# process only a few pixels
@btime jpeg_decode(filename; scale_ratio=0.25); # 77.254 ms (8 allocations: 3.23 MiB)
# process only a few pixels for luminance component
@btime jpeg_decode(Gray, filename; scale_ratio=0.25); # 63.119 ms (6 allocations: 1.08 MiB)
```
