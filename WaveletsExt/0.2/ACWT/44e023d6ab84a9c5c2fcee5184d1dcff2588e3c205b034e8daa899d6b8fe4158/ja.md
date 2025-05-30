```
acwpd(x, wt[, L])
```

与えられた信号 `x` に対して離散自己相関ウェーブレットパケット変換を実行します。ウェーブレットタイプ `wt` は変換タイプを決定します。利用可能なメソッドのリストについては、Wavelet.jlを参照してください。

# 引数

  * `x::AbstractArray{T} where T<:Number`: 元の信号で、できればサイズが 2ᴷ または (2ᴷ,2ᴹ) であることが望ましい。ここで $K, M \in \mathbb{N}$。
  * `wt::OrthoFilter`: 直交ウェーブレットフィルター。
  * `L::Integer`: (デフォルト: `maxtransformlevels(x)`) 分解のレベル数。

# 戻り値

`::Array{T}`: `x` に対する ACWPD の出力。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACWPD
acwpd(x, wt)

acwpd(x, wt, 4)
```

**関連項目:** [`iacwpd`](@ref), [`acdwt`](@ref), [`acdwt_step`](@ref)
