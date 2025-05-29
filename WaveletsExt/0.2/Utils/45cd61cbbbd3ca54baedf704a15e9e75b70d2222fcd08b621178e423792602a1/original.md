```
psnr(x, x₀)
```

Returns the peak signal to noise ratio (PSNR) between original signal x₀ and noisy signal x.

PSNR definition: $10 \log_{10} \frac{\max{(x_0)}^2}{MSE(x, x_0)}$

# Arguments

  * `x::AbstractVector{T} where T<:Number`: Signal with noise.
  * `x₀::AbstractVector{T} where T<:Number`: Reference signal.

# Returns

`::AbstractFloat`: The PSNR between x and x₀.

# Examples

```@repl
using WaveletsExt

x = randn(8)
y = randn(8)

psnr(x, y)
```

**See also:** [`relativenorm`](@ref), [`snr`](@ref), [`ssim`](@ref)
