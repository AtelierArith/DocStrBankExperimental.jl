```
struct ElectricFieldChargeDriftModel{T <: SSDFloat} <: AbstractChargeDriftModel{T}
```

Charge drift model in which the electrons and holes drift along the electric field with a mobility of ± 1m²/Vs.

This model is the default when no charge drift model is defined in the configuration file.
