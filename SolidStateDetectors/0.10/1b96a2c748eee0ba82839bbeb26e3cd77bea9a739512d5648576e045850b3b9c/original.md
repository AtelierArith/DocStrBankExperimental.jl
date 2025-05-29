```
struct NoChargeTrappingModel{T <: SSDFloat} <: AbstractChargeTrappingModel{T}
```

Charge trapping model, in which no charges are trapped during the charge drift.

This model is the default when no charge trapping model is defined in the configuration file.
