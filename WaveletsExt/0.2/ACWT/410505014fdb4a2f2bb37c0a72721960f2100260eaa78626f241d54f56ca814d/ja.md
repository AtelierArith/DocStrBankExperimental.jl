```
acdwt!(xw, x, wt, L)
```

`acdwt`と同様ですが、配列の割り当ては行いません。

# 引数

  * `xw::AbstractArray{T}`: 出力を`x`に書き込むための次元`(n,L+1)`または`(n,m,3L+1)`の割り当て済み配列。
  * `x::AbstractArray{T} where T<:Number`: 元の信号で、できればサイズは2ᴷであること（$K \in \mathbb{N}$）。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: （デフォルト: `maxtransformlevels(x)`）分解のレベル数。

# 戻り値

`xw::Array{T,2}`: `x`に対するACDWTの出力。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine, 7)
wt = wavelet(WT.haar)

# ACDWT
xw = Matrix{Float64}(undef, (128,5))
acdwt!(xw, x, wt, 4)
```

**参照:** [`acdwt`](@ref)
