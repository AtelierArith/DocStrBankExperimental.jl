```
iswpt(xw, wt[, sm])
```

逆定常ウェーブレットパケット変換 (iSWPT) を `xw` に対して計算します。

# 引数

  * `xw::AbstractArray{T,2}` または `xw::AbstractArray{T,3} where T<:Number`: SWPT変換された配列。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `sm::Integer`: `sm` が引数として含まれている場合、`sm` シフトされた逆変換が計算されます。これにより計算が大幅に高速化されますが、冗長なウェーブレット変換の強みを完全には活用できません。

# 戻り値

`::Vector{T}` または `::Matrix{T}`: 逆変換された信号。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SWPT
xw = swpt(x, wt)

# シフトベースの iSWPT
x̂ = iswpt(xw, wt, 5)

# 平均ベースの iSWPT
x̃ = iswpt(xw, wt)
```

**参照:** [`isdwt_step`](@ref), [`isdwt`](@ref), [`swpt`](@ref)
