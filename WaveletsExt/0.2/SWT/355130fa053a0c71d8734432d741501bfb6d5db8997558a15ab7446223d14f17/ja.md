```
iswpd!(x, xw, wt, L, sm)
iswpd!(x, xw, wt[, L])
iswpd!(x, xw, wt, tree, sm)
iswpd!(x, xw, wt, tree)
```

`iswpd`と同様ですが、配列の割り当ては行いません。

# 引数

  * `x::AbstractVector{T}` または `x::AbstractMatrix{T} where T<:Number`: 出力用に割り当てられた配列。
  * `xw::AbstractArray{T,2}` または `xw::AbstractArray{T,3} where T<:Number`: SWPD変換された配列。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: (デフォルト: `maxtransformlevels(x)` または `minimum(size(xw)[1:end-1]) |> maxtransformlevels`) 再構成に使用される分解レベルの数。
  * `tree::BitVector`: 逆変換が適切に計算されるためのバイナリ/クアッドツリー。
  * `sm::Integer`: `sm`が引数として含まれている場合、`sm`シフトされた逆変換が計算されます。これにより、計算が大幅に高速化されますが、冗長なウェーブレット変換の強みを完全には活用できません。

# 戻り値

`x::Vector{T}` または `x::Matrix{T}`: 逆変換された信号。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SWPD
xw = swpd(x, wt)

# ISWPD
x̂ = similar(x)
iswpd!(x̂, xw, wt, 4, 5)
iswpd!(x̂, xw, wt, maketree(x), 5)
iswpd!(x̂, xw, wt, 4)
iswpd!(x̂, xw, wt, maketree(x))
```

**参照:** [`iswpd`](@ref)
