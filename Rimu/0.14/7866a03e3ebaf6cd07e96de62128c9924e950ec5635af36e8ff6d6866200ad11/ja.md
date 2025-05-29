```
DoubleLogUpdateAfterTargetWalkers(target_walkers = 1_000, ζ = 0.08, ξ = ζ^2/4) <: ShiftStrategy
```

シフトを更新するための戦略: `target_walkers` に達した後、減衰パラメータ `ζ` と `ξ` に従ってログ式に従ってシフトを更新します。

[`DoubleLogUpdate`](@ref)、[`ShiftStrategy`](@ref)、[`ProjectorMonteCarloProblem`](@ref) を参照してください。
