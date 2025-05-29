```
acwptall(x, wt[, L])
```

信号の各スライスに対して自己相関ウェーブレットパケット変換（ACWPT）を計算します。

# 引数

  * `x::AbstractArray{T} where T<:Number`: 入力 `N-1`-D 信号、各信号は次元 `N` でスライスされます。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: （デフォルト: `minimum(size(xw)[1:end-1]) |> maxtransformlevels`）ウェーブレット変換のレベル数。

# 戻り値

  * `::Array{T}`: 変換された信号のスライス。

# 例

```julia
using Wavelets, WaveletsExt

# ランダム信号を生成
x = randn(32, 5)
# ウェーブレットを作成
wt = wavelet(WT.db4)

# xのすべての信号に対してACWPTを実行
xw = acwptall(x, wt)
```

**関連情報:** [`acwpt`](@ref)
