```
iacwpt!(x, xw[, wt])
```

`iacwpt`と同様ですが、配列の割り当ては行いません。

# 引数

  * `x::AbstractArray{T} where T<:Number`: 出力用に割り当てられた配列。
  * `xw::AbstractArray{T} where T<:Number`: ACWPD変換された配列。
  * `wt::Union{OrthoFilter, Nothing}`: (デフォルト: `nothing`) 直交ウェーブレットフィルター。

# 戻り値

`x::Array{T}`: 逆変換された信号。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACWPT
xw = acwpt(x, wt)

# IACWPT
x̂ = similar(x)
iacwpt!(x̂, xw)
```

**関連情報:** [`iacwpt`](@ref) ```
