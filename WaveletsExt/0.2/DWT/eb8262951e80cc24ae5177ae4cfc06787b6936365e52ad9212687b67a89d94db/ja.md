```
iwpdall(xw, wt[, L; standard])
iwpdall(xw, wt, tree[; standard])
```

各信号のスライスに対して逆ウェーブレットパケット分解（IWPD）を計算します。信号は、$n$次元の入力 `xw` の$n$次元目でスライスされます。

# 引数

  * `xw::AbstractArray{T} where T<:Number`: 入力信号。各スライスは1つの信号分解に対応します。次元$n$の入力信号のセット`x`に対して、`xw`は$n$次元目でスライスされます。
  * `wt::OrthoFilter`: 使用されるウェーブレット。
  * `L::Integer`: （デフォルト: `Wavelets.maxtransformlevels(xᵢ)`）ウェーブレット分解のレベル数。

# キーワード引数

  * `standard::Bool`: （デフォルト: `true`）標準のウェーブレット変換を計算するか、非標準のウェーブレット変換を計算するか。2D信号にのみ適用されます。

# 戻り値

`::Array{T}`: 分解された信号の配列。信号は最終次元でスライスされます。

# 例

```julia
using Wavelets, WaveletsExt

# ランダム信号を生成
x = randn(32, 5)
# ウェーブレットを作成
wt = wavelet(WT.db4)

# xのすべての信号に対してWPD
xw = wpdall(x, wt)

# すべての信号に対してIWPD
x̂ = iwpdall(xw, wt)
```

**関連項目:** [`wptall`](@ref), [`dwtall`](@ref), [`wpd`](@ref), [`wpd!`](@ref)
