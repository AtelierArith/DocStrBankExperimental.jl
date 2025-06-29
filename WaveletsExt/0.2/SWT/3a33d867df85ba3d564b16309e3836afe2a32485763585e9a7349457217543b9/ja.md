```
isdwt!(x, xw, wt[, sm])
```

`isdwt`と同様ですが、配列の割り当ては行いません。

# 引数

  * `x::AbstractVector{T}` または `x::AbstractMatrix{T} where T<:Number`: 再構成された信号のための割り当て。
  * `xw::AbstractArray{T,2}` または `xw::AbstractArray{T,3} where T<:Number`: SDWT変換された配列。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `sm::Integer`: `sm`が引数として含まれている場合、`sm`シフトされた逆変換が計算されます。これにより、計算が大幅に高速化されますが、冗長なウェーブレット変換の強みを完全には活用できません。

# 戻り値

`x::Vector{T}` または `x::Matrix{T}`: 逆変換された信号。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SDWT
xw = sdwt(x, wt)

# シフトベースのiSDWT
x̂ = similar(x)
isdwt!(x̂, xw, wt, 5)

# 平均ベースのiSDWT
isdwt(x̂, xw, wt)
```

**参照:** [`isdwt`](@ref)
