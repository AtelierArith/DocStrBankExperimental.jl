```
mutable struct LoadChange <: Perturbation
    time::Float64
    device::PowerSystems.ElectricLoad
    signal::Symbol
    ref_value::Float64
end
```

LoadChangeは、負荷からのアクティブまたはリアクティブパワーのセットポイントを変更することを可能にします。

# 引数:

  * `time::Float64` : Load Changeが発生する時刻を定義します。この時刻はシミュレーションで考慮される時間範囲内である必要があります。
  * `device::Type{<:PowerSystems.ElectricLoad}` : 修正される動的デバイス
  * `signal::Symbol` : どの参照セットポイントが修正されるかを決定します。受け入れられる信号は次のとおりです：

      * `:P_ref`: アクティブパワーの参照セットポイントを修正します。
      * `:Q_ref`: リアクティブパワーの参照セットポイントを修正します。
  * `ref_value::Float64` : セットポイント参照のためのユーザー定義値。
