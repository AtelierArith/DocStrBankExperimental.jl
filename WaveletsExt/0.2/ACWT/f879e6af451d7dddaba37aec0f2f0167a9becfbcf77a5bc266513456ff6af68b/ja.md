```
iacdwtall(xw[, wt])
```

各信号のスライスに対して逆自己相関離散ウェーブレット変換（IACDWT）を計算します。

# 引数

  * `xw::AbstractArray{T} where T<:Number`: ACDWT変換された信号。
  * `wt::Union{OrthoFilter, Nothing}`: （デフォルト: `nothing`）直交ウェーブレットフィルター。

# 戻り値

  * `::Array{T}`: 再構成された信号のスライス。

# 例

```julia
using Wavelets, WaveletsExt

# ランダム信号を生成
x = randn(32, 5)
# ウェーブレットを作成
wt = wavelet(WT.db4)

# xのすべての信号に対してACDWT
xw = acdwtall(x, wt)

# xwのすべての信号に対してIACDWT
x̂ = iacdwtall(xw)
```

**関連情報:** [`iacdwt`](@ref)
