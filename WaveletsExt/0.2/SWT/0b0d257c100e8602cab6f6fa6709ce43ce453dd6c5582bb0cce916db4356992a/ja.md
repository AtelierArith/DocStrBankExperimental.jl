```
swpd(x, wt[, L])
```

`x`に対して`L`レベルの定常ウェーブレットパケット分解（SWPD）を計算します。

# 引数

  * `x::AbstractVector{T}` または `x::AbstractMatrix{T} where T<:Number`: 元の信号で、サイズはできれば2ᴷであることが望ましい（$K \in \mathbb{N}$）。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: （デフォルト: `maxtransformlevels(x)`）分解のレベル数。

# 戻り値

`::Matrix{T}` または `::Array{T,3}`: `x`に対するSWPDの出力。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SWPD
xw = swpd(x, wt)
```

**関連項目:** [`iswpd`](@ref), [`swpt`](@ref)
