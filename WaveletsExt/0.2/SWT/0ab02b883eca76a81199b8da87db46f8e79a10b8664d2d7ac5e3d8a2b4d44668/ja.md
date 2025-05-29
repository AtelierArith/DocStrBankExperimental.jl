```
sdwt(x, wt[, L])
```

`L` レベルの定常離散ウェーブレット変換 (SDWT) を計算します。

# 引数

  * `x::AbstractVector{T}` または `x::AbstractMatrix{T} where T<:Number`: 元の信号で、サイズはできれば 2ᴷ であることが望ましい（$K \in \mathbb{N}$）。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: (デフォルト: `maxtransformlevels(x)`) 分解のレベル数。

# 戻り値

`::Matrix{T}` または `::Array{T,3}`: `x` に対する SDWT の出力。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SDWT
xw = sdwt(x, wt)
```

**関連項目:** [`swpd`](@ref), [`swpt`](@ref), [`isdwt`](@ref)
