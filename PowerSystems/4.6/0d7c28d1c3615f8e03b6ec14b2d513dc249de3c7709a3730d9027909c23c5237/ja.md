```
mutable struct OuterControl{
    A <: ActivePowerControl,
    R <: ReactivePowerControl
} <: DynamicInverterComponent
    active_power_control::A
    reactive_power_control::R
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

アクティブパワーコントローラーとリアクティブパワードロップコントローラーを使用したアウトループコントローラーのパラメータ。

# 引数

  * `A <: ActivePowerControl`: アクティブパワーコントローラー（通常はドロップまたは仮想慣性）。
  * `R <: ReactivePowerControl`: リアクティブパワーコントローラー（通常はドロップ）。
  * `ext::Dict{String, Any}`
  * `states::Vector{Symbol}`: 状態のベクター（コンポーネントに依存します）。
  * `n_states::Int`: 状態の数（コンポーネントに依存します）。
