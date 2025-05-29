```
swpt(x, wt[, L])
```

`x`に対して`L`レベルの定常ウェーブレットパケット変換（SWPT）を計算します。

# 引数

  * `x::AbstractVector{T}` または `x::AbstractMatrix{T} where T<:Number`: 元の信号で、サイズはできれば2ᴷであること（$K \in \mathbb{N}$）。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: （デフォルト: `maxtransformlevels(x)`）分解のレベル数。

# 戻り値

`::Matrix{T}` または `::Array{T,3}`: `x`に対するSWPTの出力。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SWPT
xw = swpt(x, wt)
```

**関連項目:** [`sdwt`](@ref), [`swpd`](@ref)
