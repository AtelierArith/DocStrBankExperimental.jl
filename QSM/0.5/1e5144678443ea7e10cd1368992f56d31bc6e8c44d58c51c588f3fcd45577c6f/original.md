```
psf2otf(
    psf::AbstractArray{<:Number, N},
    sz::NTuple{N, Integer} = size(psf);
    rfft::Bool = false,
) -> otf
```

Implementation of MATLAB's `psf2otf` function.

### Arguments

  * `psf::AbstractArray{T<:Number, N}`: point-spread function
  * `sz::NTuple{N, Integer}`: size of output array; must not be smaller than `psf`

### Keywords

  * `rfft::Bool = false`:

      * `T<:Real`: compute `fft` (`false`) or `rfft` (`true`)
      * `T<:Complex`: unused

### Returns

  * `otf`: optical transfer function
