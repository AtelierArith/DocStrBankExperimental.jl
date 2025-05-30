```
psnr(x, x₀)
```

元の信号 x₀ とノイズのある信号 x の間のピーク信号対雑音比 (PSNR) を返します。

PSNR の定義: $10 \log_{10} \frac{\max{(x_0)}^2}{MSE(x, x_0)}$

# 引数

  * `x::AbstractVector{T} where T<:Number`: ノイズのある信号。
  * `x₀::AbstractVector{T} where T<:Number`: 参照信号。

# 返り値

`::AbstractFloat`: x と x₀ の間の PSNR。

# 例

```@repl
using WaveletsExt

x = randn(8)
y = randn(8)

psnr(x, y)
```

**関連情報:** [`relativenorm`](@ref), [`snr`](@ref), [`ssim`](@ref)
