```
LogUpdateAfterTargetWalkers(target_walkers = 1_000, ζ = 0.08) <: ShiftStrategy
```

シフトを更新するための戦略: `target_walkers` に達した後、減衰パラメータ `ζ` を用いてログ式に従ってシフトを更新します。

See [`LogUpdate`](@ref), [`ShiftStrategy`](@ref), [`ProjectorMonteCarloProblem`](@ref).
