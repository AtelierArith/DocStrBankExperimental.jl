```
iacwpd(xw, L)
iacwpd(xw[, wt, L])
iacwpd(xw, tree)
iacwpd(xw, wt, tree)
```

逆自己相関離散ウェーブレットパケット変換を、分解ツリーに関して実行します。

!!! note
    逆自己相関変換はウェーブレットフィルタを必要としませんが、`wt`の位置引数が`wpt`および`swpt`との構文の標準化のために含まれていますが、信号の再構成中は無視されます。


!!! note
    この関数は、生の分解信号を再構成しようとしている場合にはあまり役に立たないかもしれません。この関数の目的は、信号が分解され（`swpd`）、しきい値処理され（`denoise`/`denoiseall`）てから再構成されるようなアプリケーションでより良く活用されるでしょう。


# 引数

  * `xw::AbstractArray{T} where T<:Number`: ACWPD変換された配列。
  * `wt::Union{OrthoFilter, Nothing}`: (デフォルト: `nothing`) 直交ウェーブレットフィルタ。
  * `L::Integer`: (デフォルト: `maxtransformlevels(x)`) 再構成に使用される分解のレベル数。
  * `tree::BitVector`: 逆変換が適切に計算されるためのバイナリツリー。

# 戻り値

`::Array{T}`: 逆変換された信号。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACWPD
xw = acwpd(x, wt)

# IACWPD
x̂ = iacwpd(xw, 4)
x̂ = iacwpd(xw, wt, 4)
x̂ = iacwpd(xw, maketree(x))
x̂ = iacwpd(xw, wt, maketree(x))
```

**参照:** [`acwpd`](@ref)
