```
iacwptall(xw[, wt])
```

信号の各スライスに対して逆自己相関ウェーブレットパケット変換（IACWPT）を計算します。

# 引数

  * `xw::AbstractArray{T} where T<:Number`: ACWPT変換された信号。
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

# xのすべての信号に対してACWPT
xw = acwptall(x, wt)

# xwのすべての信号に対してIACWPT
x̂ = iacwptall(xw)
```

**関連情報:** [`iacwpt`](@ref)
