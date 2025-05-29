```
acwpt(x, wt[, L])
```

`x`に対して`L`レベルの自己相関ウェーブレットパケット変換（ACWPT）を計算します。

# 引数

  * `x::AbstractArray{T} where T<:Number`: 元の信号で、サイズはできれば2ᴷまたは(2ᴷ,2ᴹ)であることが望ましい。ここで$K, M \in \mathbb{N}$。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: （デフォルト: `maxtransformlevels(x)`）分解のレベル数。

# 戻り値

`::Array{T}`: `x`に対するACWPTの出力。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACWPT
xw = acwpt(x, wt)
```

**関連項目:** [`iacwpt`](@ref), [`acdwt`](@ref), [`acwpd`](@ref)
