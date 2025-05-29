```
snr(x, x₀)
```

Returns the signal to noise ratio (SNR) between original signal x₀ and noisy signal x.

SNR definition: $20 \log_{10} \frac{||x_0||_2}{||x-x_0||_2}$

# Arguments

  * `x::AbstractVector{T} where T<:Number`: Signal with noise.
  * `x₀::AbstractVector{T} where T<:Number`: Reference signal.

# Returns

`::AbstractFloat`: The SNR between x and x₀.

# Examples

```@repl
using WaveletsExt

x = randn(8)
y = randn(8)

snr(x, y)
```

**See also:** [`relativenorm`](@ref), [`psnr`](@ref), [`ssim`](@ref)
