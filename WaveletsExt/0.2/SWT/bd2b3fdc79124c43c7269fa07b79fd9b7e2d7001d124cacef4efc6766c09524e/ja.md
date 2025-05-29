```
isdwt(xw, wt[, sm])
```

逆定常離散ウェーブレット変換 (iSDWT) を `xw` に対して計算します。

# 引数

  * `xw::AbstractArray{T,2}` または `xw::AbstractArray{T,3} where T<:Number`: SDWT変換された配列。
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

# SDWT
xw = sdwt(x, wt)

# シフトベースの iSDWT
x̂ = isdwt(xw, wt, 5)

# 平均ベースの iSDWT
x̃ = isdwt(xw, wt)
```

**参照:** [`isdwt_step`](@ref), [`iswpt`](@ref), [`sdwt`](@ref)
