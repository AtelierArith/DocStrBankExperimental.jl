```
fastfftsize(
    sz::NTuple{N, Integer},
    ksz::NTuple{M, Integer} = ntuple(_ -> 0, Val(N));
    rfft::Bool = false
) -> NTuple{N, Integer}
```

Next fast fft size greater than or equal to `sz` for convolution with a kernel of size `ksz`.

### Arguments

  * `x::AbstractArray{T, N}`: array to pad
  * `ksz::NTuple{M, Integer} = ntuple(_ -> 0, Val(N))`: convolution kernel size

      * `ksz[n] < 0`: no padding for dimension n

### Keywords

  * `rfft::Bool = false`: force first dimension to be even (`true`)

### Returns

  * `NTuple{N, Integer}`: fast fft size
