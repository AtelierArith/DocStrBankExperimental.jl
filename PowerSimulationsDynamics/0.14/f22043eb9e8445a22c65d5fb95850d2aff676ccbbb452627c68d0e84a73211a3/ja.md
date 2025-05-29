```
mutable struct SourceBusVoltageChange <: Perturbation
    time::Float64
    device::PSY.Source
    signal::Symbol
    ref_value::Float64
end
```

`SourceBusVoltageChange`は、電圧源によって提供される参照セットポイントを変更することを可能にします。

# 引数:

  * `time::Float64` : 制御参照変更が発生する時刻を定義します。この時刻はシミュレーションで考慮される時間範囲内である必要があります。
  * `device::Type{<:PowerSystems.Source}` : 修正されるデバイス
  * `signal::Symbol` : どの参照セットポイントが修正されるかを決定します。受け入れられる信号は次のとおりです：

      * :V_ref 内部電圧大きさの参照セットポイントを修正します。
      * :θ_ref 内部電圧角度の参照セットポイントを修正します。
  * `ref_value::Float64` : セットポイント参照のユーザー定義値。
