```
mutable struct ControlReferenceChange <: Perturbation
    time::Float64
    device::PowerSystems.DynamicInjection
    signal::Symbol
    ref_value::Float64
end
```

ControlReferenceChangeは、発電機/インバータによって提供される基準セットポイントを変更することを可能にします。

# 引数:

  * `time::Float64` : Control Reference Changeが発生する時刻を定義します。この時刻はシミュレーションで考慮される時間範囲内である必要があります。
  * `device::Type{<:PowerSystems.DynamicInjection}` : 修正される動的デバイス
  * `signal::Symbol` : どの基準セットポイントが修正されるかを決定します。受け入れられる信号は次のとおりです：

      * `:P_ref`: 有効電力基準セットポイントを修正します。
      * `:V_ref`: 電圧大きさ基準セットポイントを修正します（使用されている場合）。
      * `:Q_ref`: 無効電力基準セットポイントを修正します（使用されている場合）。
      * `:ω_ref`: 周波数セットポイントを修正します。
  * `ref_value::Float64` : セットポイント基準のユーザー定義値。
