```
struct ScaledHybridSystem{T, H <: Union{DiscreteSwitchedLinearSystem, ConstrainedDiscreteSwitchedLinearSystem}} <: HybridSystems.AbstractHybridSystem
    system::H
    γ::T
end
```

各リセットマップが `γ` でスケーリングされる離散時間システム、すなわち、`system` のリセットマップ `x ↦ Ax` が `x ↦ Ax/γ` に置き換えられます。
