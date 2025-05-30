```
snr(x, x₀)
```

元の信号 x₀ とノイズのある信号 x の間の信号対雑音比 (SNR) を返します。

SNR 定義: $20 \log_{10} \frac{||x_0||_2}{||x-x_0||_2}$

# 引数

  * `x::AbstractVector{T} where T<:Number`: ノイズのある信号。
  * `x₀::AbstractVector{T} where T<:Number`: 参照信号。

# 戻り値

`::AbstractFloat`: x と x₀ の間の SNR。

# 例

```@repl
using WaveletsExt

x = randn(8)
y = randn(8)

snr(x, y)
```

**関連情報:** [`relativenorm`](@ref), [`psnr`](@ref), [`ssim`](@ref)
