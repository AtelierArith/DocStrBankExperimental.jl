```
sixel_decode([T=RGB{N0f8}], src, [decoder]; kwargs...) -> img::IndirectArray
```

Decode the sixel format sequence provided by `src` and output as an indexed image.

# Arguments

  * `T`: output eltype. By default it is `RGB{N0f8}`.
  * `src`: the input sixel data source. It can be either an `IO`, `AbstractVector{UInt8}`, or `AbstractString`.
  * `decoder::AbstractSixelDecoder`: the sixel decoder. Currently only `LibSixelDecoder` is available.

!!! warning
    `sixel_decode` for tiny images (including vectors) is undefined behavior; sixel format requires at least `6` pixels in the row direction. For example, you should not expect it returning a `Vector` data even if it is.


# Parameters

  * `transpose::Bool`: whether we need to permute the image's width and height dimension before encoding. The default value is `false`.

# References

  * [1] VT330/VT340 Programmer Reference Manual, Volume 1: Text Programming
  * [2] VT330/VT340 Programmer Reference Manual, Volume 2: Graphics Programming
  * [3] https://github.com/saitoha/libsixel
