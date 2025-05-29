`abstract type Substance{𝗽<:PREC,𝘅<:EXAC} <: Medium{𝗽,𝘅} end`

状態方程式による物質モデルの抽象スーパタイプ。

## 階層

`Substance <: Medium <: MODELS <: AbstractTherm <: Any`
