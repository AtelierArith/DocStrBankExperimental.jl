```
TransportPropertyData(prop, T, p, ϱ, η, phase=:unknown)
ViscosityData(T, p, ϱ, η, phase=:unknown)
ThermalConductivityData(T, p, ϱ, λ, phase=:unknown)
SelfDiffusionCoefficientData(T, p, ϱ, D, phase=:unknown)
InfDiffusionCoefficientData(T, p, ϱ, D, phase=:unknown)
```

`TransportPropertyData`のコンストラクタ。圧力`p`または密度`ϱ`のいずれかを指定する必要があります。`phase`は`Vector{Symbol}`でも構いません。

## 単位

  * `[T] = K`
  * `[p] = Pa`
  * `[ϱ] = mol m⁻³`
  * `[η] = Pa s`
  * `[λ] = W (m K)⁻¹`
  * `[D] = m² s⁻¹`
