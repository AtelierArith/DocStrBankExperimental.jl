```
relativenorm(x, x₀[, p]) where T<:Number
```

元の信号 x₀ とノイズのある信号 x の間の基準 p の相対ノルムを返します。

# 引数

  * `x::AbstractArray{T} where T<:Number`: ノイズのある信号。
  * `x₀::AbstractArray{T} where T<:Number`: 参照信号。
  * `p::Real`: (デフォルト: 2) 計算される $p$-ノルム。

# 返り値

`::AbstractFloat`: x と x₀ の間の相対ノルム。

# 例

```@repl
using WaveletsExt

x = randn(8)
y = randn(8)

relativenorm(x, y)
```

**関連情報:** [`psnr`](@ref), [`snr`](@ref), [`ssim`](@ref)
