```
ssim(x, x₀)
```

Wrapper for `assess_ssim` function from ImageQualityIndex.jl.

Returns the Structural Similarity Index Measure (SSIM) between the original signal/image x₀ and noisy signal/image x.

# Arguments

  * `x::AbstractArray{T} where T<:Number`: Signal with noise.
  * `x₀::AbstractArray{T} where T<:Number`: Reference signal.

# Returns

`::AbstractFloat`: The SNR between x and x₀.

# Examples

```@repl
using WaveletsExt

x = randn(8)
y = randn(8)

ssim(x, y)
```

**See also:** [`relativenorm`](@ref), [`psnr`](@ref), [`snr`](@ref)
