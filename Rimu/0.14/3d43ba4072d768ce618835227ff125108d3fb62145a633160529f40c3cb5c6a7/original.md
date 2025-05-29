```
LogUpdateAfterTargetWalkers(target_walkers = 1_000, ζ = 0.08) <: ShiftStrategy
```

Strategy for updating the shift: After `target_walkers` is reached, update the shift according to the log formula with damping parameter `ζ`.

See [`LogUpdate`](@ref), [`ShiftStrategy`](@ref), [`ProjectorMonteCarloProblem`](@ref).
