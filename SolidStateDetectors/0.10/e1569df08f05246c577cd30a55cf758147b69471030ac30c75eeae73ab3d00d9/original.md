```
struct BoggsChargeTrappingModel{T <: SSDFloat} <: AbstractChargeTrappingModel{T}
```

Charge trapping model presented in [Boggs *et al.* (2023)](https://doi.org/10.1016/j.nima.2023.168756).

## Fields

  * `nσe::T`: Trapping product for electrons (default: `(nσe)^-1 = 1020cm`).
  * `nσh::T`: Trapping product for holes (default: `(nσh)^-1 = 2040cm`).
  * `temperature::T`: Temperature of the crystal (default: `78K`).

See also [Charge Trapping Models](@ref).
