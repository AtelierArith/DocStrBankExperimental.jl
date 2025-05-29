```
struct IsotropicChargeDriftModel{T <: SSDFloat} <: AbstractChargeDriftModel{T}
```

電場に沿って電子とホールが一定の移動度で移動する電荷ドリフトモデル

## フィールド

  * `μ_e::Union{RealQuantity, AbstractString}`: 電子の移動度 (m²/Vs)。
  * `μ_h::Union{RealQuantity, AbstractString}`: ホールの移動度 (m²/Vs)。
