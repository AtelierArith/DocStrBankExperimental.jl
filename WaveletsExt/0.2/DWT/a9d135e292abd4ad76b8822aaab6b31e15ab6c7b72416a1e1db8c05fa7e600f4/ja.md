```
iwptall(xw, wt[, L])
iwptall(xw, wt, tree)
```

各信号のスライスに対して逆ウェーブレットパケット変換（iWPT）を計算します。信号は、$n$次元入力 `xw` の$n$次元目でスライスされます。

!!! note
    `iwpt` は現在1次元および2次元信号のみに対応しています。


# 引数

  * `x::AbstractArray{T} where T<:Number`: 入力信号。各スライスは1つの信号に対応します。次元$n$の入力信号 `x` のセットに対して、信号は$n$次元目でスライスされます。
  * `wt::OrthoFilter`: 使用するウェーブレット。
  * `L::Integer`: （デフォルト: `Wavelets.maxtransformlevels(xᵢ)`）ウェーブレット分解のレベル数。
  * `tree::BitVector`: （デフォルト: `Wavelets.maketree(xᵢ, :full)`）ウェーブレット分解のために従うツリー。デフォルト値は1D信号にのみ適用されます。

# 戻り値

`::Array{T}`: 変換された信号のスライス。信号は入力信号 `x` と同じ方法でスライスされます。

# 例

```julia
using Wavelets, WaveletsExt

# ランダム信号を生成
x = randn(32, 5)
# ウェーブレットを作成
wt = wavelet(WT.db4)

# xのすべての信号に対してWPT
xw = wptall(x, wt)

# xのすべての信号に対してiWPT
x̂ = iwptall(xw, wt)
```

**関連項目:** [`wpdall`](@ref), [`dwtall`](@ref), [`wpt`](@ref)
