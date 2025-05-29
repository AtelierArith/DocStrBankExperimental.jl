```
struct ScaledHybridSystem{T, H <: Union{DiscreteSwitchedLinearSystem, ConstrainedDiscreteSwitchedLinearSystem}} <: HybridSystems.AbstractHybridSystem
    system::H
    γ::T
end
```

Discrete-time system where each reset map is scaled by `γ`, that is, the reset map `x ↦ Ax` of `system` is replaced by `x ↦ Ax/γ`.
