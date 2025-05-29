```
sixel_encode([io], src, [encoder]; kwargs...)
```

Encode colorant sequence `src` as sixel sequence and write it into a writable io-like object `io`.

# Arguments

  * `io`: the output io-like object, which is expected to be writable. Typical choices are: `stdout`, `IOBuffer` and `IOStream`. The default value is `stdout`.
  * `src`: generic container object(e.g., `AbstractArray`) that contains the colorant sequence.
  * `encoder::AbstractSixelEncoder`: the sixel encoder. Currently, only [`LibSixelEncoder`](@ref Sixel.LibSixel.LibSixelEncoder) is available.

!!! warning
    `sixel_encode` for tiny images (including vectors) is undefined behavior; sixel format requires at least `6` pixels in the row direction. For better visualization result, it's recommended to `repeat`(inner) the data so that its size is larger than `(6, 6)` in both dimensions.


!!! note
    For array with `ndims(src) >= 3`, it will be concatenated into a 2d array in row order before encoding.


# Parameters

  * `transpose::Bool`: whether we need to permute the image's width and height dimension before encoding. The default value is `false`.

# Examples

```julia
using Sixel, TestImages

# 2d RGB image
img = testimage("mandril_color")
sixel_encode(img)

# 3d RGB image will be concatenated in row order.
img3d = testimage("mri-stack")
sixel_encode(img3d)

# You can also write the encoded sixel sequences into an `IOBuffer` or `IOStream`(via `open`)
io = IOBuffer()
sixel_encode(io, img)
println(String(take!(io)))

open("out.sixel", "w") do io
    sixel_encode(io, img)
end
```

# References

  * [1] VT330/VT340 Programmer Reference Manual, Volume 1: Text Programming
  * [2] VT330/VT340 Programmer Reference Manual, Volume 2: Graphics Programming
  * [3] https://github.com/saitoha/libsixel
