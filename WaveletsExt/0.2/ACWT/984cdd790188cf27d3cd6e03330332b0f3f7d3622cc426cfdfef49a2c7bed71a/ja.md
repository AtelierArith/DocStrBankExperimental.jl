```
iacwpdall(xw[, wt, L])
iacwpdall(xw, L)
iacwpdall(xw, wt, tree)
iacwpdall(xw, tree)
```

信号の各スライスに対して逆自己相関ウェーブレットパケット分解（IACWPD）を計算します。

# 引数

  * `xw::AbstractArray{T} where T<:Number`: ACWPD変換された信号。
  * `wt::Union{OrthoFilter, Nothing}`: （デフォルト: `nothing`）直交ウェーブレットフィルター。
  * `L::Integer`: （デフォルト: `minimum(size(xw)[1:end-2]) |> maxtransformlevels`）ウェーブレット変換のレベル数。
  * `tree::BitVector`: 逆変換を計算するためのバイナリツリー。

# 戻り値

  * `::Array{T}`: 再構成された信号のスライス。

# 例

```julia
using Wavelets, WaveletsExt

# ランダム信号を生成
x = randn(32, 5)
# ウェーブレットを作成
wt = wavelet(WT.db4)

# xのすべての信号に対してACWPD
xw = acwpdall(x, wt)

# xwのすべての信号に対してIACWPD
x̂ = iacwpdall(xw)
x̂ = iacwpdalll(xw, maketree(x))
x̂ = iacwpdall(xw, 5)
```

**参照:** [`iacwpd`](@ref)
