```
sdwt!(xw, x, wt[, L])
```

`sdwt`と同様ですが、配列の割り当ては行いません。

# 引数

  * `xw::AbstractArray{T,2}` または `xw::AbstractArray{T,3} where T<:Number`: `x`の出力を書き込むための次元が`(n,L+1)`の割り当て済み配列。
  * `x::AbstractVector{T}` または `x::AbstractMatrix{T} where T<:Number`: 元の信号で、できればサイズは2ᴷであること（$K \in \mathbb{N}$）。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: (デフォルト: `maxtransformlevels(x)`) 分解のレベル数。

# 戻り値

`xw::Array{T,2}` または `xw::Array{T,3}`: `x`に対するSDWTの出力。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine, 7)
wt = wavelet(WT.haar)

# SDWT
xw = Matrix{Float64}(undef, (128,5))
sdwt!(xw, x, wt, 4)
```

**参照:** [`sdwt`](@ref)
