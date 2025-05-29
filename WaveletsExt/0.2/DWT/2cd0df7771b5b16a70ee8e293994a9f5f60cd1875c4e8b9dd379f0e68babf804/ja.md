```
wpdall(x, wt[, L])
```

各信号のスライスに対してウェーブレットパケット分解（WPD）を計算します。信号は、$n$次元の入力`x`の$n$次元目でスライスされます。

# 引数

  * `x::AbstractArray{T} where T<:Number`: 入力信号。各スライスは1つの信号に対応します。次元$n$の入力信号`x`のセットに対して、信号は$n$次元目でスライスされます。
  * `wt::OrthoFilter`: 使用されるウェーブレット。
  * `L::Integer`: （デフォルト: `minimum(size(x)[1:end-1]) |> maxtransformlevels`）ウェーブレット分解のレベル数。

# 戻り値

`::Array{T}`: 分解された信号の配列。信号は最終次元でスライスされます。

# 例

```julia
using Wavelets, WaveletsExt

# ランダム信号を生成
x = randn(32, 5)
# ウェーブレットを作成
wt = wavelet(WT.db4)

# xのすべての信号に対してWPT
xw = wpdall(x, wt)
```

**関連項目:** [`wptall`](@ref), [`dwtall`](@ref), [`wpd`](@ref), [`wpd!`](@ref)
