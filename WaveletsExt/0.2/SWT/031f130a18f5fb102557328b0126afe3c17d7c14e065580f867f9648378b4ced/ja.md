```
sdwtall(x, wt[, L])
```

各信号のスライスに対して定常離散ウェーブレット変換（SDWT）を計算します。

# 引数

  * `x::AbstractArray{T} where T<:Number`: 入力 `N-1`-D 信号、各信号は次元 `N` でスライスされます。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: （デフォルト: `Wavelets.maxtransformlevels(xᵢ)`）ウェーブレット変換のレベル数。

# 戻り値

  * `::Array{T}`: 変換された信号のスライス。

# 例

```julia
using Wavelets, WaveletsExt

# ランダム信号を生成
x = randn(32, 5)
# ウェーブレットを作成
wt = wavelet(WT.db4)

# x のすべての信号に対して SDWT
xw = sdwtall(x, wt)
```

**関連情報:** [`sdwt`](@ref)
