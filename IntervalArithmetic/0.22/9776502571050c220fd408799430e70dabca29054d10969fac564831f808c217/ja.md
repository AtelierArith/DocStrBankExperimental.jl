```
Interval{T<:NumTypes} <: Real
```

IEEE標準1788-2015に従った区間演算による計算が保証された区間型。この構造体は、[`BareInterval`](@ref)と[`Decoration`](@ref)を組み合わせたものです。

フィールド:

  * `bareinterval :: BareInterval{T}`
  * `decoration   :: Decoration`
  * `isguaranteed :: Bool`

IEEE標準1788-2015に準拠したコンストラクタ:

  * [`interval`](@ref)
  * [`..`](@ref)
  * [`±`](@ref)
  * [`@I_str`](@ref)

参照: [`±`](@ref), [`..`](@ref) および [`@I_str`](@ref).
