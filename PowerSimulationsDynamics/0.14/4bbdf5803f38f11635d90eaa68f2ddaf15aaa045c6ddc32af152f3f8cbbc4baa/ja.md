```
mutable struct GeneratorTrip <: Perturbation
    time::Float64
    device::PowerSystems.DynamicInjection
end
```

`GeneratorTrip`は、指定された時間に動的発電ユニットをシステムから切り離すことを可能にします。

# 引数:

  * `time::Float64` : Generator Tripが発生する時刻を定義します。この時間はシミュレーションで考慮される時間範囲内である必要があります。
  * `device::Type{<:PowerSystems.DynamicInjection}` : 切り離されるデバイス
