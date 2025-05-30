```
iacwpd!(x, xw, L)
iacwpd!(x, xw[, wt, L])
iacwpd!(x, xw, tree)
iacwpd!(x, xw, wt, tree)
```

`iacwpd`と同様ですが、配列の割り当ては行いません。

# 引数

  * `x::AbstractArray{T} where T<:Number`: 出力用に割り当てられた配列。
  * `xw::AbstractArray{T} where T<:Number`: ACWPD変換された配列。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: (デフォルト: `maxtransformlevels(x)`) 再構成に使用される分解レベルの数。
  * `tree::BitVector`: 逆変換を計算するためのバイナリツリー。

# 戻り値

`x::Array{T}`: 逆変換された信号。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACWPD
xw = acwpd(x, wt)

# IACWPD
x̂ = similar(x)
iacwpd!(x̂, xw, 4)
iacwpd!(x̂, xw, wt, 4)
iacwpd!(x̂, xw, maketree(x))
iacwpd!(x̂, xw, wt, maketree(x))
```

**参照:** [`iacwpd`](@ref)
