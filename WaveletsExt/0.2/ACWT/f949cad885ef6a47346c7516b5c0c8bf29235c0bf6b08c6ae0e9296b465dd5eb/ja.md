```
acwpd!(xw, x, wt[, L])
```

`acwpd`と同様ですが、配列の割り当ては行いません。

# 引数

  * `xw::AbstractArray{T} where T<:Number`: 出力用に割り当てられた配列。
  * `x::AbstractArray{T} where T<:Number`: 元の信号で、できればサイズは2ᴷで$K \in \mathbb{N}$であることが望ましい。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: (デフォルト: `maxtransformlevels(x)`) 分解のレベル数。

# 戻り値

`xw::Array{T}`: `x`に対するACWPDの出力。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACWPD
xw = Matrix{Float64}(undef, (128, 255))
acwpd!(xw, x, wt)
acwpd!(xw, x, wt, 7)
```

**関連情報:** [`acwpd!`](@ref)
