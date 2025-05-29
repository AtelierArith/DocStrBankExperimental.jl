```
iswpdall(xw, wt, L, sm)
iswpdall(xw, wt[, L])
iswpdall(xw, wt, tree, sm)
iswpdall(xw, wt, tree)
```

信号の各スライスに対して逆自己相関ウェーブレットパケット分解（ISWPD）を計算します。

# 引数

  * `xw::AbstractArray{T} where T<:Number`: SWPD変換された信号。
  * `wt::Union{OrthoFilter, Nothing}`: （デフォルト: `nothing`）直交ウェーブレットフィルター。
  * `L::Integer`: （デフォルト: `minimum(size(xw)[1:end-2]) |> maxtransformlevels`）ウェーブレット変換のレベル数。
  * `tree::BitVector`: 逆変換がそれに応じて計算されるバイナリツリー。
  * `sm::Integer`: `sm`が引数として含まれている場合、`sm`シフトされた逆変換が計算されます。これにより、計算が大幅に高速化されますが、冗長なウェーブレット変換の強みを完全には活用できません。

# 戻り値

  * `::Array{T}`: 再構成された信号のスライス。

# 例

```julia
using Wavelets, WaveletsExt

# ランダム信号を生成
x = randn(32, 5)
# ウェーブレットを作成
wt = wavelet(WT.db4)

# xのすべての信号に対してSWPD
xw = swpdall(x, wt)

# xwのすべての信号に対してISWPD
x̂ = iswpdall(xw)
x̂ = iswpdalll(xw, maketree(x))
x̂ = iswpdall(xw, 5)
```

**参照:** [`iswpd`](@ref)
