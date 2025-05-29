```julia
Constant(
    _::Type{BigFloat},
    units::Vector{Unitful.FreeUnits{N, D, nothing} where {N, D}}
) -> PhysicalParticles.Constant

```

`BigFloat` に対応する基本的な物理定数を `units` に格納する不変構造体を構築します（デフォルトは `uAstro` です）。
