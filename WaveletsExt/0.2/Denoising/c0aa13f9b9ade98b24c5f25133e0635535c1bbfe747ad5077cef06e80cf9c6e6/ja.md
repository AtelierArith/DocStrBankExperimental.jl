```
SureShrink(xw[, redundant, tree, th])
```

`SureShrink`の構造体コンストラクタは、信号係数`xw`に基づいています。

# 引数

  * `xw::AbstractArray{T} where T<:Number`: 分解された信号。
  * `redundant::Bool`: (デフォルト: `false`) `xw`の変換タイプが冗長変換であるかどうか。自己相関や定常ウェーブレット変換は冗長変換の例です。
  * `tree::Union{BitVector, Nothing}`: (デフォルト: `nothing`) `xw`を分解するための基底ツリー。`xw`が`wpt`、`swpd`、または`acwpd`を使用して分解されている場合は提供する必要があります。
  * `th::Wavelets.Threshold.THType`: (デフォルト: `HardTH()`) 閾値タイプ。

# 戻り値

`::SureShrink`: SUREShrinkオブジェクト。

# 例

```julia
SureShrink(xw)                  # `xw`はdwt、wptの出力
SureShrink(xw, true)            # `xw`はsdwt、acdwt、swpt、acwpdの出力
SureShrink(xw, true, tree)      # `xw`はswpd、acwpdの出力
```

**関連情報:** [`SureShrink`](@ref), [`surethreshold`](@ref)
