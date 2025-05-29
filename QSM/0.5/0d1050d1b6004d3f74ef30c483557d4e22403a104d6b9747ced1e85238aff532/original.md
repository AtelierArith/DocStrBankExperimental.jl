```
padfastfft(
    x::AbstractArray{T, N},
    ksz::NTuple{M, Integer} = ntuple(_ -> 0, Val(N));
    pad::Symbol = :fill,
    val = zero(T),
    rfft::Bool = false,
) -> typeof(similar(x, szp))
```

Pad array `x` to a fast fft size for convolution with a kernel of size `ksz`, keeping the array centered at `n÷2+1`.

### Arguments

  * `x::AbstractArray{T, N}`: array to pad
  * `ksz::NTuple{M, Integer} = ntuple(_ -> 0, Val(N))`: convolution kernel size

      * `ksz[n] < 0`: no padding for dimension n

### Keywords

  * `pad::Symbol = :fill`: padding method

      * `:fill`
      * `:circular`
      * `:replicate`
      * `:symmetric`
      * `:reflect`
  * `val = 0`: pads array with `val` if `pad = :fill`
  * `rfft::Bool = false`: force first dimension to be even (`true`)

### Returns

  * `typeof(similar(x, szp))`: padded array
