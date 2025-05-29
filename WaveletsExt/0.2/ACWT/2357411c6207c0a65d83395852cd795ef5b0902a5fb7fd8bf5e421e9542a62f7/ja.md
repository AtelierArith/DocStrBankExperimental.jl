```
acwpt!(xw, x, wt[, L])
```

`acwpt`と同様ですが、配列の割り当ては行いません。

# 引数

  * `xw::AbstractArray{T} where T<:Number`: 変換された信号のための割り当て。
  * `x::AbstractArray{T} where T<:Number`: 元の信号で、サイズはできれば2ᴷまたは(2ᴷ,2ᴹ)であることが望ましい。ここで$K, M \in \mathbb{N}$。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: (デフォルト: `maxtransformlevels(x)`) 分解のレベル数。

# 戻り値

`xw::Array{T}`: `x`に対するACWPTの出力。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACWPT
xw = Array{Float64,2}(undef, (128,128))
acwpt!(xw, x, wt)
```

**参照:** [`acwpt`](@ref), [`iacwpt`](@ref)
