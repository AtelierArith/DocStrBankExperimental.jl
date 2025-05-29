```
iswptall(xw[, wt])
iswptall(xw, wt, sm)
```

各信号のスライスに対して逆定常ウェーブレットパケット変換（ISWPT）を計算します。

# 引数

  * `xw::AbstractArray{T} where T<:Number`: SWPT変換された信号。
  * `wt::Union{OrthoFilter, Nothing}`: （デフォルト: `nothing`）直交ウェーブレットフィルター。
  * `sm::Integer`: `sm`が引数として含まれている場合、`sm`シフトされた逆変換が計算されます。これにより計算が大幅に高速化されますが、冗長なウェーブレット変換の強みを完全には活用できません。

# 戻り値

  * `::Array{T}`: 再構成された信号のスライス。

# 例

```julia
using Wavelets, WaveletsExt

# ランダム信号を生成
x = randn(32, 5)
# ウェーブレットを作成
wt = wavelet(WT.db4)

# xのすべての信号に対してSWPT
xw = swptall(x, wt)

# xwのすべての信号に対してISWPT
x̂ = iswptall(xw)
```

**関連項目:** [`iswpt`](@ref)
