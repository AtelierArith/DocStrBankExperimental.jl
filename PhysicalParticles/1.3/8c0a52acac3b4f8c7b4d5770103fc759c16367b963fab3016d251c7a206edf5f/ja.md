```julia
Constant(
    _::Type{Measurements.Measurement},
    units::Vector{Unitful.FreeUnits{N, D, nothing} where {N, D}}
) -> PhysicalParticles.Constant

```

`units`に対応する`Measurement`の基本物理定数を格納する不変構造体を構築します（デフォルトは`uAstro`です）。
