```
iacwpt(xw[, wt])
```

`xw`に対して逆自己相関ウェーブレットパケット変換（IACWPT）を計算します。

!!! note
    逆自己相関変換はウェーブレットフィルタを必要としませんが、`wpt`および`swpt`との構文の標準化のためにオプションの`wt`位置引数が含まれていますが、信号の再構成中は無視されます。


# 引数

  * `xw::AbstractArray{T} where T<:Number`: ACWPT変換された配列。
  * `wt::Union{OrthoFilter, Nothing}`: （デフォルト: `nothing`）直交ウェーブレットフィルタ。

# 戻り値

`::Array{T}`: 逆変換された信号。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACWPT
xw = acwpt(x, wt)

# IACWPT
x̃ = iacwpt(xw)
```

**参照:** [`iacdwt`](@ref), [`acwpt`](@ref)
