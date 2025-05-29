```
iacdwt(xw[, wt])
```

逆自己相関離散ウェーブレット変換を実行します。1Dおよび2Dの両方のケースで使用できます。

!!! note
    逆自己相関変換はウェーブレットフィルターを必要としませんが、`dwt`および`sdwt`との構文の標準化のためにオプションの`wt`位置引数が含まれていますが、信号の再構築中は無視されます。


# 引数

  * `xw::AbstractArray{T} where T<:Number`: ACDWT変換された配列。
  * `wt::Union{OrthoFilter, Nothing}`: (デフォルト: `nothing`) 直交ウェーブレットフィルター。

# 戻り値

`::Array{T}`: 逆変換された信号。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACDWT
xw = acdwt(x, wt)

# IACDWT
x̃ = iacdwt(xw)
```

**参照:** [`acdwt`](@ref), [`iacdwt_step!`](@ref)
