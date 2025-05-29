```
swpd!(xw, x, wt[, L])
```

`swpd`と同様ですが、配列の割り当ては行いません。

# 引数

  * `xw::AbstractArray{T,2}` または `xw::AbstractArray{T,3} where T<:Number`: 変換された信号のための割り当て。
  * `x::AbstractVector{T}` または `x::AbstractMatrix{T} where T<:Number`: 元の信号で、できればサイズは 2ᴷ で $K \in \mathbb{N}$ であること。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: (デフォルト: `maxtransformlevels(x)`) 分解のレベル数。

# 戻り値

`xw::Matrix{T}` または `xw::Array{T,3}`: `x` に対する SWPD の出力。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SWPD
xw = Matrix{T}(undef, (128, 255))
swpd!(xw, x, wt)
```

**参照:** [`swpd`](@ref)
