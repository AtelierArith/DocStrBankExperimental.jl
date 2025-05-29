```
DoubleLogUpdateAfterTargetWalkers(target_walkers = 1_000, ζ = 0.08, ξ = ζ^2/4) <: ShiftStrategy
```

Strategy for updating the shift: After `target_walkers` is reached, update the shift according to the log formula with damping parameter `ζ` and `ξ`.

See [`DoubleLogUpdate`](@ref), [`ShiftStrategy`](@ref), [`ProjectorMonteCarloProblem`](@ref).
