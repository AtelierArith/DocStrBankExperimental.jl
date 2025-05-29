```
acdwt(x, wt[, L])
```

与えられた信号 `x` に対して離散自己相関ウェーブレット変換を実行します。信号は1Dまたは2Dです。ウェーブレットタイプ `wt` は変換タイプを決定します。利用可能なメソッドのリストについては、Wavelet.jlを参照してください。

# 引数

  * `x::AbstractArray{T} where T<:Number`: 元の信号で、できればサイズは2ᴷであること（$K   \in \mathbb{N}$）。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: （デフォルト: `maxtransformlevels(x)`）分解のレベル数。

# 戻り値

`::Array{T}`: `x` に対するACDWTの出力。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACDWT
acdwt(x, wt)
acdwt(x, wt, 4) # レベル4の分解
```

**関連項目:** [`acdwt_step`](@ref), [`iacdwt`](@ref), [`acdwt!`](@ref)
