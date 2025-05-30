```
ssim(x, x₀)
```

`ImageQualityIndex.jl`の`assess_ssim`関数のラッパーです。

元の信号/画像x₀とノイズのある信号/画像xとの間の構造類似性指数（SSIM）を返します。

# 引数

  * `x::AbstractArray{T} where T<:Number`: ノイズのある信号。
  * `x₀::AbstractArray{T} where T<:Number`: 参照信号。

# 返り値

`::AbstractFloat`: xとx₀の間のSNR。

# 例

```@repl
using WaveletsExt

x = randn(8)
y = randn(8)

ssim(x, y)
```

**関連情報:** [`relativenorm`](@ref), [`psnr`](@ref), [`snr`](@ref)
