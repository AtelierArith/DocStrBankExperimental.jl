```
combine(frames...; method = median, [hdu = 1], [header_hdu = 1])
combine(frames; method = median, [hdu = 1], [header_hdu = 1])
```

Combine multiple frames using `method`. Multiple frames can also be passed in a vector or as generators for combining.

To pass a custom method, it must have a signature like `method(::AbstractArray; dims)`.

If `frames` are strings, they will be loaded into [`CCDData`](@ref)s first. The HDU indices can be specified with `hdu` as either an integer or a tuple corresponding to each file.

Header of output file (if applicable) is specified by `header_hdu` which by default is 1.

# Examples

```jldoctest
julia> frame = [reshape(1.0:4.0, (2, 2)) for i = 1:4];

julia> combine(frame)
2×2 Matrix{Float64}:
 1.0  3.0
 2.0  4.0

julia> combine(frame, method = sum)
2×2 Matrix{Float64}:
 4.0  12.0
 8.0  16.0

```
