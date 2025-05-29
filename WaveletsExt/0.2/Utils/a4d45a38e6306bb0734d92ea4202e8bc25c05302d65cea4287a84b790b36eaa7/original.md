```
relativenorm(x, x₀[, p]) where T<:Number
```

Returns the relative norm of base p between original signal x₀ and noisy signal x.

# Arguments

  * `x::AbstractArray{T} where T<:Number`: Signal with noise.
  * `x₀::AbstractArray{T} where T<:Number`: Reference signal.
  * `p::Real`: (Default: 2) $p$-norm to be computed.

# Returns

`::AbstractFloat`: The relative norm between x and x₀.

# Examples

```@repl
using WaveletsExt

x = randn(8)
y = randn(8)

relativenorm(x, y)
```

**See also:** [`psnr`](@ref), [`snr`](@ref), [`ssim`](@ref)
