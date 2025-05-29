```
mutable struct LoadTrip <: Perturbation
    time::Float64
    device::PowerSystems.ElectricLoad
end
```

`LoadTrip`は、ユーザーがシステムから負荷を切り離すことを可能にします。

# 引数:

  * `time::Float64` : ジェネレーターのトリップが発生する時刻を定義します。この時刻はシミュレーションで考慮される時間範囲内である必要があります。
  * `device::Type{<:PowerSystems.ElectricLoad}` : 切り離されるデバイス
