```
dwtall(x, wt[, L])
```

各信号のスライスに対して離散ウェーブレット変換（DWT）を計算します。信号は、$n$次元入力`x`の$n$次元目でスライスされます。

!!! note
    `dwt`は現在、1-D、2-D、および3-D信号のみに対応しています。


# 引数

  * `x::AbstractArray{T} where T<:Number`: 入力信号。各スライスは1つの信号に対応します。次元$n$の入力信号`x`のセットに対して、信号は$n$次元目でスライスされます。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: （デフォルト: `Wavelets.maxtransformlevels(xᵢ)`）ウェーブレット変換のレベル数。

# 戻り値

`::Array{T}`: 変換された信号のスライス。信号は入力信号`x`と同じ方法でスライスされます。

# 例

```julia
using Wavelets, WaveletsExt

# ランダム信号を生成
x = randn(32, 5)
# ウェーブレットを作成
wt = wavelet(WT.db4)

# xのすべての信号に対してDWTを実行
xw = dwtall(x, wt)
```

**関連項目:** [`idwtall`](@ref), [`wpdall`](@ref), [`wptall`](@ref)
